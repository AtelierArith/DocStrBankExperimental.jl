```
ancestralreconstruction(obj::SSM, trait::Integer = 1)
```

離散的特徴番号 `trait`（デフォルトでは最初の特徴）の祖先状態の周辺確率を推定します。[`StatisticalSubstitutionModel`](@ref) オブジェクト `obj` のパラメータは、最初に [`fitdiscrete`](@ref) を使用してフィッティングされる必要があり、祖先状態の再構築は推定されたパラメータに条件付けられます。これらのパラメータがすべての特徴を使用して推定された場合、それらはそのまま使用され、関心のある特定の `trait` の祖先状態の再構築が行われます。

**出力**: ノード番号のための最初の列、ノードラベルのための2番目の列、各可能な状態のための列を持つデータフレーム：これらの列のエントリは、特定のノードが特定の状態を持つ周辺確率を示します。

警告:

  * ノード番号とノードラベルは `obj.net` のものであり、これは `obj` を構築するために使用された元のネットワークとは異なる内部表現を持つ可能性があります。
  * `obj` は変更されます：その尤度フィールド（前方、方向性、後方）は、`obj.model` の現在のパラメータ値に対応するように更新され、関心のある `trait` に対応します。

制限: 以下はチェックされません。

  * 大きなネットワークのすべてのノードが、表示される各ツリーにも存在することを前提としています。これは、ネットワークがツリー子でない場合には真ではありません...
  * ルートも表示される各ツリーに存在することを前提としていますが、ルートがハイブリッド子エッジを持っていた場合にはそうでないかもしれません。

[`posterior_logtreeweight`](@ref) および [`discrete_backwardlikelihood_trait!`](@ref) も参照して、`obj.backwardlik` を更新してください。

# 例

```jldoctest
julia> net = readnewick("(((A:2.0,(B:1.0)#H1:0.1::0.9):1.5,(C:0.6,#H1:1.0::0.1):1.0):0.5,D:2.0);");

julia> m1 = BinaryTraitSubstitutionModel([0.1, 0.1], ["lo", "hi"]);

julia> using DataFrames

julia> dat = DataFrame(species=["C","A","B","D"], trait=["hi","lo","lo","hi"]);

julia> fit1 = fitdiscrete(net, m1, dat);

julia> asr = ancestralreconstruction(fit1)
9×4 DataFrame
 Row │ nodenumber  nodelabel  lo        hi
     │ Int64       String     Float64   Float64
─────┼───────────────────────────────────────────
   1 │          1  A          1.0       0.0
   2 │          2  B          1.0       0.0
   3 │          3  C          0.0       1.0
   4 │          4  D          0.0       1.0
   5 │          5  5          0.286021  0.713979
   6 │          6  6          0.319456  0.680544
   7 │          7  7          0.16855   0.83145
   8 │          8  8          0.767359  0.232641
   9 │          9  H1         0.782776  0.217224

julia> using PhyloPlots

julia> plot(fit1.net, nodelabel = asr[!,[:nodenumber, :lo]], tipoffset=0.2); # pp for "lo" state
```
