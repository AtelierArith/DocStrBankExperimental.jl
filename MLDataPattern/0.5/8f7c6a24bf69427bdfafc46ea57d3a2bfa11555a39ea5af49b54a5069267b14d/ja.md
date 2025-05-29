```
DataSubset(data, [indices], [obsdim])
```

# 説明

任意の型の `data` のサブセットを表すために使用され、サブセットがどの観測インデックスを跨いでいるかを保存します。さらに、実際のデータにアクセスすることなく、後続のサブセッティングが蓄積されます。

`DataSubset` の存在の主な目的は、実際のデータのバッチ（または単一の観測）が計算のために必要になるまで、データへのアクセスと移動を遅延させることです。これは、データがメモリに存在せず、ハードドライブやリモートの場所にある場合に特に便利です。このようなシナリオでは、必要なデータを必要なときにのみロードしたいと考えます。

この型は通常手動で構築されることはなく、代わりに [`datasubset`](@ref)、[`shuffleobs`](@ref)、または [`splitobs`](@ref) を呼び出すことでインスタンス化されます。

`data` が `Tuple` の場合、コンストラクタはその要素に対してマッピングされます。つまり、コンストラクタは `Tuple` の `DataSubset` を返すのではなく、`DataSubset` の `Tuple` を返します。

# 引数

  * **`data`** : データセットを説明するオブジェクト。`getobs`](@ref) と [`nobs`](@ref) を実装している限り、任意の型で構いません（詳細については詳細を参照してください）。
  * **`indices`** : オプション。サブセットが表すべき `data` 内の観測のインデックスまたはインデックス。`Int` 型または `AbstractVector` のサブタイプであることができます。
  * **`obsdim`** : オプション。`data` の型に意味がある場合、`obsdim` を使用して `data` のどの次元が観測を示すかを指定できます。型安定な方法で位置引数として指定することも（`?LearnBase.ObsDim` を参照）、より便利にスマートキーワード引数として指定することもできます。

# メソッド

  * **`getindex`** : 指定されたインデックス/インデックスの観測を新しい `DataSubset` として返します。必要なインデックス以外のデータはコピーされません。
  * **`nobs`** : サブセット内の観測の総数を返します（**全体のデータセットではありません**）。
  * **`getobs`** : 指定された相対インデックスで `DataSubset` が表す基礎データを返します。これらのインデックスは「サブセット空間」にあり、一般的には基礎データセット内の同じインデックスに直接対応しません。

# 詳細

`DataSubset` がデータ構造で機能するためには、望ましい型 `MyType` が以下のインターフェースを実装する必要があります：

  * `LearnBase.getobs(data::MyType, idx, [obsdim::ObsDimension])` : `idx` でインデックスされた観測を返す必要があります。どのような形式で返すかはユーザー次第です。`idx` は `Int` または `AbstractVector` 型であることができます。
  * `StatsBase.nobs(data::MyType, [obsdim::ObsDimension])` : `data` 内の観測の総数を返す必要があります。

以下のメソッドも提供可能であり、オプションです：

  * `LearnBase.getobs(data::MyType)` : デフォルトではこの関数は恒等関数です。それがあなたの型に対して望ましい動作でない場合は、このメソッドも提供する必要があります。
  * `LearnBase.datasubset(data::MyType, idx, obsdim::ObsDimension)` : カスタム型が独自のサブセット型を持っている場合、ここでそれを返すことができます。そのようなケースの例は、`AbstractArray` のサブセットを表すための `SubArray` です。注意：型が `obsdim` を必要としない場合は、シグネチャで `::ObsDim.Undefined` にディスパッチします。
  * `LearnBase.getobs!(buffer, data::MyType, [idx], [obsdim::ObsDimension])` : `getobs(data, idx, obsdim)` のインプレースバージョン。このメソッドが `MyType` に対して提供されている場合、`eachobs` および `eachbatch`（他のものの中で）で、各イテレーションで再利用されるバッファを事前に割り当てることができます。注意：`buffer` は `getobs(::MyType, ...)` の戻り値と同等であるべきです。これは、`buffer` がデフォルトでどのように事前に割り当てられるかを示しています。
  * `LearnBase.gettargets(data::MyType, idx, [obsdim::ObsDimension])` : `MyType` に `getobs` を呼び出すことなくターゲットをクエリする特別な方法がある場合、ここで独自のロジックを提供できます。これは、ターゲットが常にメタデータとしてロードされ、データ自体は実際に必要になるまでハードディスクに残る場合に便利です。

# 著者

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# 例

```julia
X, y = MLDataUtils.load_iris()

# アイリスセットには150の観測と4つの特徴があります
@assert size(X) == (4,150)

# 80の観測を DataSubset として表します
subset = DataSubset(X, 21:100)
@assert nobs(subset) == 80
@assert typeof(subset) <: DataSubset
# getobs はサブセットにインデックスを付けます
@assert getobs(subset, 1:10) == X[:, 21:30]

# 他の次元を使用して観測を示すデータでも作業できます。
@assert size(X') == (150,4)
subset = DataSubset(X', 21:100, obsdim = :first) # または "obsdim = 1"
@assert nobs(subset) == 80

# obsdim を型安定な方法で指定するには、サブモジュール `ObsDim` によって提供される位置引数を使用します。
@inferred DataSubset(X', 21:100, ObsDim.First())

# サブセットはデータのタプルにも適用されます。（ラベル付きデータに便利）
subset = DataSubset((X,y), 1:100)
@assert nobs(subset) == 100
@assert typeof(subset) <: Tuple # DataSubset のタプル

# 小文字バージョンは、配列などのカスタム「サブセット」を提供する型に対して DataSubset へのボクシングを避けようとします。
# ここでは、代わりにネイティブな SubArray を作成します。
subset = datasubset(X, 1:100)
@assert nobs(subset) == 100
@assert typeof(subset) <: SubArray

# 任意の長さのタプルにも適用されます
subset = datasubset((X,y), 1:100)
@assert nobs(subset) == 100
@assert typeof(subset) <: Tuple # SubArray のタプル

# データセットをトレーニングとテストに分割
train, test = splitobs(shuffleobs((X,y)), at = 0.7)
@assert typeof(train) <: Tuple # SubArray の
@assert typeof(test)  <: Tuple # SubArray の
@assert nobs(train) == 105
@assert nobs(test) == 45
```

# 参照

[`datasubset`](@ref)、[`getobs`](@ref)、[`nobs`](@ref)、[`splitobs`](@ref)、[`shuffleobs`](@ref)、[`KFolds`](@ref)、[`BatchView`](@ref)、[`ObsView`](@ref)、
