---
description: >-
  Kotlin’i Java’ya nazaran daha kullanışlı, avantajlı (ve havalı) kılan nedir,
  Kotlin'in avantajları nelerdir, neden Android için Kotlin kullanmalıyız?
  (kotlin vs java, java vs kotlin).
---

# 🚀 Kotlin'in Java'ya Göre Avantajları \(Kotlin vs Java\)

![](../.gitbook/assets/kotlin.png)

## 🏂 Kotlin Dünyasına Giriş

* 👁️ Açık kaynaklıdır \(Java 13 kapalı, _openJDK hariç_\)
* 🕰️ Java 8 eskidir, java 13 çıkmıştır
* 🚀 Proje Kotlin dahi olsa Java sınıfları oluşturabilirsin
* 💫 Java kodlarını `Convert Java File to Kotlin` komutu ile Kotlin kodlarına çevirebilirsin
* 💁‍♂️ Tüm paketi çevirmek için paketi seç ve bu komutu kullan
* 👀 Neden geçmen gerektiğini öğrenmek için yazıyı okumaya devam et

{% hint style="warning" %}
📢 Çok büyük projeleri parça parça geçirmeniz tavsiye edilir
{% endhint %}

## ✨ Değişken Tanımlaması

* 💦 Java'daki `final` yapısı yerine daha sade bir arayüz sunar
* 🚀 Değişken türlerinin tanımlanmasına gerek yoktur
* 😱 Fonksiyon değişkenleri tanımlanabilir
* ⚡ Statik değişkenler için scope sunar
* 🕐 Daha sonra tanımlanacak değişkenler oluşturulabilir \(`lateinit`\)

> 🧐 Size birini mi anımsattı? \([🐍 Python](https://python.yemreak.com)\)

```kotlin
var metin = "yemreak" // String metin = "yemreak"
var metin: String = "yemreak" // String metin = "yemraek"
val metin = "değişmem" // final String metin = "değişmem"

/*
Foo
bar
*/
val uzunMetin = """
                Foo
                Bar
                """.trimIndent()

/*
if(a > 1) {
    return a
}
*/               
val uzunGirintiliMetin = """if(a > 1) {
                         |    return a
                         |}""".trimMargin()

var func: () -> Unit = {
    // Kardeş ben fonksiyonum
}

var func2: (Boolean) -> Unit = { bool ->
    // Kardeş ben parametreli fonksiyonum
}

var func2: (Boolean) -> Int = { bool ->
    // Kardeş ben bir integer döndürüyorum
    return 1
}

companion object {
    var metin = "yemreak" // static String metin = "yemreak"
    var metin: String = "yemreak" // static String metin = "yemraek"
    val metin = "değişmem" // static final String metin = "değişmem"
}

lateinit var sonrakiMetin
// ... 
sonrakiMetin = "yok"

// 0 sa true değilse false
val isEmpty: Boolean get() = size == 0
```

## 🐥 Nullable Objeler

* ✨ Java'daki `NullPointerException` hatalarına odaklı bir çalışmadır
* 🌌 Objeler null olabilir veya null olamaz şeklinde oluşturulur
* 💁‍♂️ Default olarak null olamaz olarak atanır

```kotlin
var metin: String = "selam" // var metin = "selam" ile aynıdır
var metin: String? = null
metin?. // Varsa kullan
metin!! // Olduğundan kesinlikle eminim

var func: (() -> Unit)? = null
func?.invoke() // Null değilse çalıştır

// Dsoya varsa sayısı yoksa boş yaz
println(files?.size ?: "empty")

// Hata fırlatmalı atamalar
val email = values["email"] ?: throw IllegalStateException("Email is missing!")
```

## 🍎 Veri Sınıfları

* 📈 Kotlin `class` veya `data class` yapısı ile `get` ve `set` kullanımı gerekmez
* 🙄 Java ile resmin solundaki yapı gereklidir

![](../.gitbook/assets/kotlin_dataclass.png)

## 🐣 Get Set Kullanımı

* 🌌 Get set olmadan direkt olarak kullanabilirsiniz
* ‍🧙‍♂ Kotlin, onu sizin için halletmekte

```kotlin
val arrayAdapter = ArrayAdapter<String>(
    wifiDirectActivity,
    R.layout.activity_wifi_direct,
    deviceNameList
)
wifiDirectActivity.lvPeer.adapter = arrayAdapter
```

## 👮‍♂️ Switch - Case

* 🤝 Koşullu değer atama işlemlerini destekler
* 📈 Sıradan switch yapısına göre daha verimlidir

```kotlin
val reasonMsg = when (reason) {
    WifiP2pManager.P2P_UNSUPPORTED -> "P2P desteklenmiyor"
    WifiP2pManager.ERROR -> "hata oluştur"
    WifiP2pManager.BUSY -> "cihaz başka bir bağlantı ile meşgul"
    else -> ""
}
```

## 💁‍♂️ Functional Arguments

* 💦 Gereksiz yere parantez `(` kullanımı yoktur
* ⚙️ Bu yapı ile otomatik olarak **son fonksiyona** tanımlanan işlemler atanır

```kotlin
button.setOnClickListener { view ->
    // ...
}

/*
// Java kullanımı
button.setOnClickListener ( { view ->

});
*/

fun funcT(func1: () -> Unit, func2 () -> Unit) { }

funcT({ /* func1 */ }) {
    // func2
}
```

{% hint style="warning" %}
📢 Functional argument olursa, sadece `metot {}` kullanılması durumunda sadece son argümana değer atanır
{% endhint %}

## ➕ Function Extension

* 💁‍♂️ Tanımlı olan sınıflara `.` operatörü ile metotlar ekleyebilirsiniz
* 👇 Alttaki örnekte `Uri` sınıfına `getInputStream` metodu ekliyoruz

> 📢 `Uri` sınıfı temel java sınıflarından birisidir

![](../.gitbook/assets/kotlin_function_extension.png)

{% hint style="success" %}
🚀 Android Kotlin Extension'ları [Android KTX](https://developer.android.com/kotlin/ktx/extensions-list) paketi altındadır
{% endhint %}

## 🔪 Dizileri Parçalama

* 🎯 Range metodu kullanılarak diziler parçalanabilmekte
* 🐥 Çok kolay kullanımı vardır

> 🐍 Python dizi parçalama işlemlerine benzemektedir

```kotlin
val byteArray = ByteArray()
val slicedByteArray: List<Byte> = BUFFER.slice(3..5)

val bas = 10
val son = 100
val slicedByteArray2: List<Byte> = BUFFER.slice(bas..son)
```

## 💱 Dizileri Dönüştürme

* 🚀 `toTypedArray`eklentisi ile direkt olarak List'i argümana çevirebilirsiniz

> 📈 Java'dan çok daha verimli

```kotlin
val quakes: List<Quake> 
val args: Array<out Quake> = quakes.toTypedArray()

/* Java 
List<String> yourList = List.of("hello", "world");
yourVarargMethod(yourList.toArray(new String[0]));
*/
```

{% hint style="info" %}
‍🧙‍♂ Detaylı bilgi için [Fonksiyonlar](../fonksiyonlar.md) alanına bakabilirsin.
{% endhint %}

## 💎 Keyword Argument

* ✨ Değişkenlerin adları ile onlara değer atayabilirsin
* ⭐ Python gibi dillerde olan bir kullanımdır

```kotlin
hasWifiDirectPermission(activity = activity)

fun hasWifiDirectPermission(activity: Activity): Boolean {
    return hasPermission(
        activity,
        Manifest.permission.ACCESS_FINE_LOCATION
    )
}
```

{% hint style="warning" %}
📢 Functional argument olursa, sadece `metot {}` kullanılması durumunda sadece son argümana değer atanır
{% endhint %}

## 💠 Parametre Olarak Fonksiyon

* 💁‍♂️ Fonksiyonlar obje ise parametre olarak da kullanılabilir
* 💡 [Tanımlama şekli](kotlin-vs-java.md#degisken-tanimlamasi) ile parametre olarak verilebilir

```kotlin
fun func(inFunc: (ByteArray) -> Unit) {
   // ...
   inFunc()
}

// Func kullanımı
func {
   // inFunc içeriği
]

var func2 = { byteArray -> /* ... */ }
func(func2) 

```

## 👨‍💼 Run - Apply - Let - Also

* 👪 Bir değişkenin birden fazla metodunu kullanmayı sağar
* 🐣 Apply objelerine değer atarsınız
* ▶️ Run ile alt metotlarını kullanırsın, sonucunu döndürürsünüz
* 🙋‍♂️ Let ile objeyi koşullu kullanabilirsin
* 💁‍♂️ Also ile "işlemi bitirmeden bir de bunu yap" deriz
* 📈 Tekrar tekrar yazmayı engeller

```kotlin
val wifiFilter = IntentFilter().apply {
    addAction(WifiP2pManager.WIFI_P2P_STATE_CHANGED_ACTION)
    addAction(WifiP2pManager.WIFI_P2P_PEERS_CHANGED_ACTION)
}

obje.run {
    metot2() // obje.metot2()
    metot3() // obje.metot3() Döndürülür
}

obje?.let { // Koşullu kullanım
    it.metot2() // obje.metot2()
    it.metot3() // obje.metot3()
}

channel?.also { channel ->
    wifiReceiver = WifiDirectBroadcastReceiver(manager, channel, this)
}

// Yer değiştirme
a = b.also { b = a }
```

{% hint style="info" %}
‍🧙‍♂ Detaylı bilgi için [Scope Function](https://kotlinlang.org/docs/reference/scope-functions.html#functions) ve [Function Selections](https://kotlinlang.org/docs/reference/scope-functions.html#functions) alanlarına bakabilirsin.
{% endhint %}

## 👀 Dokümantasyon Linkleri

* 👇 Metotların üzerine geldiğinizde \(hover\) açıklamasında doküman linki olur
* ⭐ Link üzerinden kullanım örneklerine erişirsiniz

![](../.gitbook/assets/kotlin_ktdoc.png)

## 📃 XML ID'lerini Koda Import Etme

* 🔗 Kotlin otomatik olarak xml idlerini projeye dahil eder
* 👨‍💻 `import kotlinx.android.synthetic.main.<layour>.*` ile dahil edilir
* 💦 `findViewByID` metoduna gerek yoktur

![](../.gitbook/assets/image%20%281%29.png)

## 👮‍♂️ İzinlerin Kontrolü

* 📢 İzin tanımlanmadığında hata verir
* 💁‍♂️ `@SupressLint("MissingPermission")` ile bunu engelleyebilirsiniz
* 🤭 "Ne yaptığımın farkındayım, bana bulaşma" demek gibi

![](../.gitbook/assets/kotlin_permission.png)

## 🚧 Coroutine

* 🕊️ Thread işlemlerini kolaylaştıran bir hafif yapıdır
* 👷‍♂️ `Coroutine` ile inline thread kullanabilirsin
* 👮‍♂️ Main \(UI\), IO, Default thread yapıları ile arka plan işlemlerini yönetirsiniz
* ✨ Otomatik olarak optimize edilirler

| 🧱 Dispatchers.Main | 🔣 Dispatchers.IO | 🎳 Dispatchers.Default |
| :--- | :--- | :--- |
| UI Thread işlemleri | Disk ve network işlemleri | CPU gerektiren işlemler |
| Fonksiyon çağırma | Database | Liste sıralama |
| View işlemleri | Dosya okuma & yazma | JSON parsing |
| LiveData işlemleri | Ağ işlemleri | DiffUtils |

{% hint style="info" %}
‍🧙‍♂ Detaylı bilgi için [Coroutine](../coroutine/) alanına bakabilirsin.
{% endhint %}

## 🗃️ RoomDB Coroutine Scope

* 👮‍♂️ `suspend` anahtar kelimesi ile thread gerektiren metotlar belirlenir
* ❌ Thread gerektiren metotlar UI Thread üzerinde çalıştırılamaz
* 🌌 Coroutine scope içerisinde kendilerine özgü thread ile çalıştırılır
* 👋 `AsyncTask`'a elveda \(_zaten sevmedim_ 🙄\)

{% code title="ViewModel" %}
```kotlin
fun refreshQuakes(quakes: List<Quake>) = viewModelScope.launch {
   repository.deleteAll() // Dao üzerinden suspend metottur
   repository.insert(quakes.toTypedArray())
}

/*
@Dao
abstract class QuakeDao {
	
	@Query("DELETE FROM ${Quake.TABLE_NAME}")
	abstract suspend fun deleteAll() // Burada suspend ile thread istiyoruz
	
}
*/
```
{% endcode %}

{% hint style="info" %}
‍🧙‍♂ Detaylı bilgi için [RoomDB - Android](https://android.yemreak.com/veriler/room-database) sayfasına bakabilirsin.
{% endhint %}

## 🔗 Faydalı Kaynaklar

* [👨‍💻 From Java to kotlin](https://github.com/MindorksOpenSource/from-java-to-kotlin)

## 🧐 Daha Fazla

{% embed url="https://kotlin.yemreak.com/" %}

{% embed url="https://medium.com/@yedhrab/kotlinin-java-ya-g%C3%B6re-avantajlar%C4%B1-3e88ab5620bf" %}

{% embed url="https://github.com/MindorksOpenSource/from-java-to-kotlin" %}



