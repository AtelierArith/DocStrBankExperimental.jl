### CarouselArray{T}

  * dims::Vector{T}

`CarouselArray`は、片側またはもう片側に無限にインデックスを付けることができる配列です。インデックスは、"dims"内に格納された`Vector`の他の端にロールオーバーします。

##### 例

```
mycarousel = CarouselArray([5, 10, 15, 20])

mycarousel[1]
5
mycarousel[0]
20
mycarousel[-1]
15
mycarousel[4]
20
mycarousel[5]
5
```

---

##### フィールド情報

  * **dims** - `CarouselArray`の内部`Vector`。

---

##### コンストラクタ

  * CarouselArray{T}()
  * CarouselArray{T}(x::AbstractVector)
  * CarouselArray(x::AbstractVector)
