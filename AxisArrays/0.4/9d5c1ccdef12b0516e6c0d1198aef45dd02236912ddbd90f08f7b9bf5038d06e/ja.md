AxisArrayは、別のAbstractArrayをラップし、各配列次元に軸名と値を追加するAbstractArrayです。AxisArrayは、次元による位置インデックスの代わりに名前付き軸を使用してインデックス付けできます。軸値に沿った他の高度なインデックス付けも提供されています。

### 型パラメータ

AxisArrayは、いくつかの型パラメータを含みます：

```julia
struct AxisArray{T,N,D,Ax} <: AbstractArray{T,N}
```

  * `T` : AbstractArrayの要素型
  * `N` : 次元の数
  * `D` : ラップされたAbstractArrayの型
  * `Ax` : 軸の名前と型、(特化された) NTuple{N, Axis}として

### コンストラクタ

```julia
AxisArray(A::AbstractArray, axes::Axis...)
AxisArray(A::AbstractArray, names::Symbol...)
AxisArray(A::AbstractArray, vectors::AbstractVector...)
AxisArray(A::AbstractArray, (names...,), (steps...,), [(offsets...,)])
```

### 引数

  * `A::AbstractArray` : ラップされた配列データ
  * `axes` または `names` または `vectors` : ラップされた配列の次元情報

次元情報は3つの方法のいずれかで渡すことができ、完全にオプションです。次元の軸名または値が欠けている場合、デフォルトが代わりに使用されます。次元 `(1, 2, 3, 4, 5, ...)` のデフォルト軸名は `(:row, :col, :page, :dim_4, :dim_5, ...)` です。デフォルトの軸値は、各欠けている次元 `d` に対して `Base.axes(A, d)` です。

### インデックス付け

インデックス付けは、元のデータへのビューを返します。返されるビューは、SubArrayをラップした新しいAxisArrayです。インデックス付けは型安定であるべきです。特定の軸に基づいてインデックス付けするには、`Axis{axisname}(idx)` を使用します。`axisname` はインデックス/スライスする軸を指定するシンボルで、`idx` は通常のインデックスオブジェクト（`Int`、`Array{Int,1}`など）またはその特定の軸のためのカスタムインデックス型です。

デフォルトでサポートされている主な2つの軸のタイプは次のとおりです：

  * カテゴリカル軸 – これは通常、シンボルまたは文字列のラベルのベクトルです。要素またはスライスは、要素または要素のベクトルによってインデックス付けできます。
  * 次元軸 – これは、`ClosedInterval()` によってインデックス付けできるソートされたベクトルまたはイテレータです。これは、時間または日付時刻のシーケンスに一般的に使用されます。通常のサンプルレートの場合、範囲を使用できます。

ユーザー定義の軸型は、カスタムインデックス動作とともに追加できます。カテゴリカルまたは次元軸としてカスタム型を追加するには、[`AxisArrays.axistrait`](@ref)を使用してトレイトを追加します。

より高度なインデックス付けのために、[`AxisArrays.axisindexes`](@ref)のカスタムメソッドを定義できます。

### 例

次に、行に沿った時間シーケンスを表す次元軸（FloatRange）と、列ヘッダーのシンボルのカテゴリカル軸を持つ例を示します。

```julia
A = AxisArray(reshape(1:15, 5, 3), Axis{:time}(.1:.1:0.5), Axis{:col}([:a, :b, :c]))
A[Axis{:time}(1:3)]   # A[1:3,:] と同等
A[Axis{:time}(ClosedInterval(.2,.4))] # 時間軸に沿ったAxisArrayを制限
A[ClosedInterval(0.,.3), [:a, :c]]   # 区間と2つの列を選択
```
