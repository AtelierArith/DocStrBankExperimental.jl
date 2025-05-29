```
@index
```

`@index`マクロは、カーネル関数内のワークアイテムのインデックスを取得するために使用できます。線形インデックスまたは直交インデックスの生成の両方をサポートしています。直交インデックスは、イテレーション空間から導出される一般的なN次元インデックスです。

# インデックスの粒度

  * `Global`: グローバルメモリにアクセスするために使用されます。
  * `Group`: `workgroup`のインデックス。
  * `Local`: `workgroup`内のインデックス。

# インデックスの種類

  * `Linear`: メモリに線形インデックスを付けるために使用できる`Int64`を生成します。
  * `Cartesian`: メモリにインデックスを付けるために使用できる`CartesianIndex{N}`を生成します。
  * `NTuple`: メモリにインデックスを付けるために使用できる`NTuple{N}`を生成します。

インデックスの種類が指定されていない場合、デフォルトは`Linear`であり、これは変更される可能性があります。

# 例

```julia
@index(Global, Linear)
@index(Global, Cartesian)
@index(Local, Cartesian)
@index(Group, Linear)
@index(Local, NTuple)
@index(Global)
```
