```
ルール
```

`Rule`オブジェクトは、シミュレーションのすべてのタイムステップのすべてのセルに`applyrule`メソッドを適用するために必要な情報を含んでいます。

[`applyrule`](@ref)メソッドは次の形式に従います：

```julia
@inline applyrule(data::AbstractSimData, rule::MyRule, state, I::Tuple{Int,Int}) = ...
```

ここで、`I`はセルインデックスであり、`state`は単一の値、または複数のグリッドが要求される場合は`NamedTuple`です。[`AbstractSimData`](@ref)オブジェクトは、現在のタイムステップやその他のシミュレーションデータおよびメタデータにアクセスするために使用できます。

ルールは、各タイムステップの前に元のルールから更新できます。これは[`modifyrule`](@ref)で行います。ここでは、パラメータがグリッドの合計に依存します：

```jldoctest
using DynamicGrids, Setfield
struct MySummedRule{R,W,T} <: CellRule{R,W}
    gridsum::T
end
function modifyrule(rule::MySummedRule{R,W}, data::AbstractSimData) where {R,W}
    Setfield.@set rule.gridsum = sum(data[R])
end

# 出力
modifyrule (generic function with 1 method)
```

ルールは、`Tuple`として、または[`Ruleset`](@ref)として連続して実行することもできます。

DynamicGridsは次のことを保証します：

  * `modifyrule`は、各タイムステップのすべてのルールに対して1回実行されます。結果は`applyrule`に渡されますが、その後は保持されません。
  * `applyrule`は、すべてのルールに対して、すべてのセル、すべてのタイムステップで1回実行されます。空のセルをスキップするために[`SparseOpt`](@ref)のような最適化が使用されない限り。
  * 任意のセルに対してルールを実行した結果は、グリッド内の他の場所で同じルールを実行する際の入力に影響を与えません。
  * シーケンス内の後のルールには、前のルールによって更新されたグリッド状態が渡されます。
  * マスクされた領域や、ラップされたまたは削除された`boundary`領域は、変更があった場合にルール間で更新されます。

## 複数のグリッド

初期の`NamedTuple`のキーは、各ルールの`R`および`W`で使用されるグリッドキーと一致します。これは`Tuple{:key1,:key1}`のような型です。名前はユーザーが指定するものであり、`Rule`によって固定されるべきではありません。

読み取りグリッド名は、ここでの型から`R1`および`R2`として取得され、書き込みグリッドは`W1`および`W2`です。

```jldoctest
using DynamicGrids
struct MyMultiSetRule{R,W} <: SetCellRule{R,W} end
function applyrule(
    data::AbstractSimData, rule::MyMultiSetRule{Tuple{R1,R2},Tuple{W1,W2}}, (r1, r2), I
) where {R1,R2,W1,W2}
    add!(data[W1], 1, I) 
    add!(data[W2], 1, I) 
end

# 出力
applyrule (generic function with 1 method)
```

`applyrule`の戻り値は、指定された`W`書き込みグリッドの現在のセルに書き込まれます。複数のグリッドに書き込む`Rule`は、単に`W`型パラメータで指定された順序の`Tuple`を返します。

## ルールのパフォーマンス

ルールはシミュレーション中に何百万回も実行される可能性があります。迅速である必要があります。ルールを書くための基本的なガイドラインは次のとおりです：

  * 可能な限り`Rule`内でメモリを割り当てないでください。
  * 型の安定性は不可欠です。[`isinferred`](@ref)は、ルールが型安定であるかどうかを確認するのに役立ちます。
  * `applyrule`に`@inline`マクロを使用すると、シミュレーションにコードをインライン化するのを強制するのに役立ちます。
  * 複数のグリッドからの読み取りおよび書き込みは、高速キャッシュメモリへの追加の負荷のために高価です。使用するグリッドの数を制限するようにしてください。
  * ProfileView.jlのようなグラフィカルプロファイラを使用して、`sim!`で実行したときのルールの全体的なパフォーマンスを確認してください。
