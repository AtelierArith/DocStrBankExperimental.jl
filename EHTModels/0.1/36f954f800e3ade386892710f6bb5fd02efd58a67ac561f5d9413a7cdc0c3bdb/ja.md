```
AbstractModel
```

抽象モデルタイプ。独自のモデルタイプをインスタンス化するには、このモデルからサブタイプを作成する必要があります。さらに、インターフェースを満たすために以下のメソッドを実装する必要があります: **必須メソッド**

  * [`isprimitive`](@ref): モデルがスタンドアロンであるか、他のモデルに基づいて定義されているかを定義します。モデルがプリミティブである場合、これは `IsPrimitive()` を返すべきです。そうでない場合は `NotPrimitive()` を返します。
  * [`visanalytic`](@ref): モデルの可視性が解析的に計算できるかどうかを定義します。もし可能であれば、これは `IsAnalytic()` を返し、ユーザーは `visibility_point` を定義する必要があります。解析的でない場合、`visanalytic` は `NotAnalytic()` を返すべきです。
  * [`imanalytic`](@ref): モデルの強度が点ごとに計算できるかどうかを定義します。もし可能であれば、これは `IsAnalytic()` を返し、ユーザーは `intensity_point` を定義する必要があります。解析的でない場合、`imanalytic` は `NotAnalytic()` を返すべきです。
  * [`radialextent`](@ref): 画像領域におけるモデルの放射範囲の推定値を提供します。これは画像のサイズを推定するためや、プロットに使用されます。
  * [`flux`](@ref): モデルの総フラックスを返します。

**オプションメソッド:**

  * [`intensity_point`](@ref): モデルの強度を点ごとに計算する方法を定義します。これは `imanalytic(::Type{YourModel})==IsAnalytic()` の場合に定義する必要があります。
  * [`visibility_point`](@ref): モデルの可視性を点ごとに計算する方法を定義します。これは `visanalytic(::Type{YourModel})==IsAnalytic()` の場合に定義する必要があります。
  * [`_visibilities`](@ref): 追加の速度を得ることができる場合の `visibility_point` のベクトル化バージョン
  * [`intensitymap`](@ref): モデルの全画像を計算します
  * [`intensitymap!`](@ref): `intensitymap` のインプレースバージョン
