```
AbstractDVec{K,V}
```

スパースストレージを持つベクトルのようなデータ構造のための抽象データ型。概念的には、`AbstractDVec`sはスカラー型`V`上のベクトル空間の要素を表しますが、辞書に似て任意の型`K`（非整数である可能性もある）によってインデックス付けされます。これらは、[VectorInterface.jl](https://github.com/Jutho/VectorInterface.jl)からのインターフェースをサポートし、[`ProjectorMonteCarloProblem`](@ref Main.ProjectorMonteCarloProblem)を用いた量子モンテカルロや、[KrylovKit](https://github.com/Jutho/KrylovKit.jl)を用いた行列フリー線形代数にうまく機能するように設計されています。

具体的な実装は、[`PDVec`](@ref Main.DictVectors.PDVec)、[`DVec`](@ref Main.DictVectors.DVec)、および[`InitiatorDVec`](@ref Main.DictVectors.InitiatorDVec)として利用可能です。

`AbstractDVec`sは、`FCIQMC`における生成アルゴリズムを選択する[`StochasticStyle`](@ref)を持っています。`AbstractDVec`に保存されていない要素を検索するとゼロが返され、値をゼロに設定するとベクトルから削除されるべきです。`AbstractDVec`を反復処理するには、`keys`、`pairs`、または`values`を使用します。可能な場合は、`sum`や`mapreduce`などの還元関数を使用してください。

# インターフェース

インターフェースは`AbstractDict`インターフェースに似ていますが、上記のように動作が変更されています。`AbstractDict`インターフェースに必要なもの（`pairs`、`keys`、`values`、`setindex!`、`getindex`、`delete!`、`length`、`empty`、`empty!`）を実装し、さらに以下を追加します：

  * [`StochasticStyle`](@ref)
  * [`storage`](@ref)は、生データを異なる`valtype`で保存する`AbstractDict`を返します。
  * [`deposit!`](@ref)

[VectorInterface.jl](https://github.com/Jutho/VectorInterface.jl)インターフェースのためのデフォルト実装は、上記の関数を通じて提供されています。

さらに[`DictVectors`](@ref Main.DictVectors)、[`Interfaces`](@ref)も参照してください。
