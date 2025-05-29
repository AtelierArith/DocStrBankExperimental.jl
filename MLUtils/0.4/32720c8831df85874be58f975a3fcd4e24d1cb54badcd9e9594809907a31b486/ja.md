```
ObsView(data, [indices])
```

任意の型の一部の `data` のサブセットを表すために使用され、サブセットがどの観測インデックスを跨いでいるかを保存します。さらに、実際のデータにアクセスすることなく、後続のサブ設定が蓄積されます。

`ObsView` の存在の主な目的は、実際のデータのバッチ（または単一の観測）が計算のために必要になるまで、データへのアクセスと移動を遅延させることです。これは、データがメモリに存在せず、ハードドライブやリモートの場所にある場合に特に便利です。このようなシナリオでは、必要なデータを必要なときにのみロードしたいと考えます。

データへのアクセスは `getindex` が呼び出されるまで遅延され、さらに `getindex` は一般的にデータの移動を回避する [`obsview`](@ref) の結果を返します。イテレータとして使用される場合、ビューはデータセットを一度だけ反復し、効果的にエポックを示します。各反復は現在の観測に対する遅延サブセットを返します。

# 引数

  * **`data`** : データセットを説明するオブジェクト。 [`getobs`](@ref) と [`numobs`](@ref) を実装している限り、任意の型で構いません（詳細については詳細を参照してください）。
  * **`indices`** : オプション。サブセットが表すべき `data` 内の観測のインデックスまたはインデックスのリスト。 `Int` 型または `AbstractVector` のサブタイプである必要があります。

# メソッド

  * **`getindex`** : 指定されたインデックス/インデックスの観測を返します。必要なインデックス以外のデータはコピーされません。
  * **`numobs`** : サブセット内の観測の総数を返します。
  * **`getobs`** : 指定された相対インデックスで `ObsView` が表す基礎データを返します。これらのインデックスは「サブセット空間」にあり、一般的には基礎データセットの同じインデックスに直接対応しません。

# 詳細

`ObsView` がデータ構造で機能するためには、望ましい型 `MyType` が以下のインターフェースを実装する必要があります：

  * `getobs(data::MyType, idx)` : `idx` でインデックスされた観測を返す必要があります。どのような形式で返すかはユーザー次第です。 `idx` は `Int` 型または `AbstractVector` である可能性があります。
  * `numobs(data::MyType)` : `data` 内の観測の総数を返す必要があります。

以下のメソッドも提供可能であり、オプションです：

  * `getobs(data::MyType)` : デフォルトではこの関数は恒等関数です。これがあなたの型に対して望む動作でない場合は、このメソッドも提供する必要があります。
  * `obsview(data::MyType, idx)` : カスタム型が独自のサブセット型を持っている場合、ここでそれを返すことができます。そのような場合の例は、いくつかの `AbstractArray` のサブセットを表すための `SubArray` です。
  * `getobs!(buffer, data::MyType, [idx])` : `getobs(data, idx)` のインプレースバージョン。このメソッドが `MyType` に対して提供されている場合、`eachobs` は各反復で再利用されるバッファを事前に割り当てることができます。注意：`buffer` は `getobs(::MyType, ...)` の戻り値と同等である必要があります。これは、`buffer` がデフォルトでどのように事前に割り当てられるかを示しています。

# 例

```julia
X, Y = MLUtils.load_iris()

# アイリスセットには150の観測と4つの特徴があります
@assert size(X) == (4,150)

# 80の観測を ObsView として表します
v = ObsView(X, 21:100)
@assert numobs(v) == 80
@assert typeof(v) <: ObsView
# getobs は v にインデックスを付けます
@assert getobs(v, 1:10) == X[:, 21:30]

# `obsview` を使用して ObsView にボクシングするのを避けます
# カスタム「サブセット」を提供する型に対して、配列など。
# ここでは代わりにネイティブな SubArray を作成します。
v = obsview(X, 1:100)
@assert numobs(v) == 100
@assert typeof(v) <: SubArray

# 任意の長さのタプルにも対応
subset = obsview((X, Y), 1:100)
@assert numobs(subset) == 100
@assert typeof(subset) <: Tuple # SubArray のタプル

# イテレータとして使用
for x in ObsView(X)
    @assert typeof(x) <: SubArray{Float64,1}
end

# 各個別のラベル付き観測を反復
for (x, y) in ObsView((X, Y))
    @assert typeof(x) <: SubArray{Float64,1}
    @assert typeof(y) <: String
end

# 同じだがランダムな順序で
for (x, y) in ObsView(shuffleobs((X, Y)))
    @assert typeof(x) <: SubArray{Float64,1}
    @assert typeof(y) <: String
end

# インデクシング：最初の10の観測を取得
x, y = ObsView((X, Y))[1:10]
```

# 参照

[`obsview`](@ref),  [`getobs`](@ref), [`numobs`](@ref), [`splitobs`](@ref), [`shuffleobs`](@ref), [`kfolds`](@ref).
