```
FoldsView(data, train_indices, val_indices, [obsdim])
```

# 説明

`data`のベクトルのような表現を作成します。ここで、各個別要素は、トレーニングサブセットとバリデーションサブセットのタプルの形で`data`のパーティションです。

`FoldsView`の目的は、事前に計算されたサブセット割り当てインデックスのシーケンスを、便利な方法でデータコンテナに適用することです。`FoldsView`自体は、特定の再分配戦略（k-フォールドなど）には無関係です。代わりに、`train_indices`と`val_indices`は、そのような戦略によって事前に計算され、具体的な`data`コンテナとともに`FoldsView`に渡される必要があります。結果として得られるオブジェクトは、`getindex`を使用して個々のフォールドを照会するか、単に反復処理することができます。

# 引数

  * **`data`** : データセットを説明するオブジェクト。`[`getobs`](@ref)`と`[`nobs`](@ref)`を実装している限り、任意のタイプで構いません（詳細については、詳細を参照してください）。
  * **`train_indices`** : トレーニング割り当てのシーケンスを含む整数ベクトルのベクトル。この要素は、各*トレーニング*サブセットを説明するインデックスのベクトルです。このベクトルの長さは`val_indices`と一致する必要があります。
  * **`val_indices`** : バリデーション割り当てのシーケンスを含む整数ベクトルのベクトル。この要素は、各*バリデーション*サブセットを説明するインデックスのベクトルです。このベクトルの長さは`train_indices`と一致する必要があります。
  * **`obsdim`** : オプション。`data`のタイプに意味がある場合、`obsdim`を使用して`data`のどの次元が観測を示すかを指定できます。位置引数として型安定な方法で指定することも（`?LearnBase.ObsDim`を参照）、より便利にスマートキーワード引数として指定することもできます。

# 詳細

`FoldsView`がデータ構造で機能するためには、望ましいタイプ`MyType`が以下のインターフェースを実装する必要があります：

  * `LearnBase.getobs(data::MyType, idx, [obsdim::ObsDimension])` : `idx`でインデックスされた観測を返す必要があります。どのような形式で返すかはユーザー次第です。`idx`は`Int`または`AbstractVector`の型である可能性があります。
  * `StatsBase.nobs(data::MyType, [obsdim::ObsDimension])` : `data`内の観測の総数を返す必要があります。

# 著者

  * Christof Stocker (Github: https://github.com/Evizero)
  * Tom Breloff (Github: https://github.com/tbreloff)

# 例

```
# デモ用にアイリスデータをロード
X, y = MLDataUtils.load_iris()

# kfoldsを使用してトレーニングおよびバリデーションパーティションインデックスを計算
train_idx, val_idx = kfolds(nobs(X), 10)

# これらの2つのベクトルは、各パーティショニングのインデックスベクトルを含んでいます
@assert typeof(train_idx) <: Vector{Vector{Int64}}
@assert typeof(val_idx)   <: Vector{UnitRange{Int64}}
@assert length(train_idx) == length(val_idx) == 10

# 再分配をイテレータとして使用
for (train_X, val_X) in FoldsView(X, train_idx, val_idx)
    @assert size(train_X) == (4, 135)
    @assert size(val_X) == (4, 15)
end

# データセットでkfoldsを呼び出すと
# FoldsViewが自動的に作成されます。
# したがって、このコードは上記と同等です
for (train_X, val_X) in kfolds(X, 10)
    @assert size(train_X) == (4, 135)
    @assert size(val_X) == (4, 15)
end

# leaveoutはk = nobs(X)を設定するためのショートカットです
for (train_X, val_X) in leaveout(X)
    @assert size(val_X) == (4, 1)
end
```

# 参照

[`kfolds`](@ref), [`leaveout`](@ref), [`splitobs`](@ref), [`DataSubset`](@ref)
