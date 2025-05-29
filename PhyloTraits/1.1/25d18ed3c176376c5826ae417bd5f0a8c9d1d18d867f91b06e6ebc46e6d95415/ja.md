```
fitdiscrete(net, model, tipdata)
fitdiscrete(net, model, RateVariationAcrossSites, tipdata)
fitdiscrete(net, model, species, traits)
fitdiscrete(net, model, RateVariationAcrossSites, species, traits)
fitdiscrete(net, model, dnadata, dnapatternweights)
fitdiscrete(net, model, RateVariationAcrossSites, dnadata, dnapatternweights)
fitdiscrete(net, modSymbol, species, traits)
fitdiscrete(net, modSymbol, dnadata, dnapatternweights)
```

ネットワークまたは木に対して、先端に1つ以上の離散的なキャラクターが与えられた場合の最大尤度（ML）スコアを計算します。各エッジに沿って、遷移は連続時間マルコフ `model` でモデル化され、そのパラメータは尤度を最大化することによって推定されます。各ハイブリッドノードでは、特性は2つの直近の親のいずれかから、親の平均遺伝的寄与（遺伝 γ）に従って継承されると仮定されます。このモデルは不完全な系統選択を無視します。アルゴリズムはネットワークに表示されるすべての木を抽出します。

データは次のいずれかの形式で与えることができます：

  * `tipdata`: 辞書 taxon => 状態ラベル、単一の特性の場合。
  * `tipdata`: 単一の特性のデータフレーム。この場合、分類名は列1に表示されるか、「taxon」または「species」という名前の列に表示され、特性 *ラベル* は列2に表示されるか、「trait」という名前の列に表示される必要があります。ここで、特性ラベルは `getlabels(model)` に表示されるようにする必要があります。
  * `species`: 文字列のベクトル、`traits`: 特性のDataFrame、行は種名の順序に対応します。再度、特性ラベルは `getlabels(model)` に表示されるようにする必要があります。すべての特性は同じモデルに従い、同じパラメータを持つと仮定されます。
  * `dnadata`: readfastatodnaの出力の最初の部分、列1に分類名があり、各サイトの列があるBioSequence DNA配列のデータフレーム。
  * `dnapatternweights`: readfastatodnaの出力の2番目の部分、各サイト列の1つの重みの配列。重みの長さはnsitesに等しいです。dnapatternweightsを使用する場合は、dnadataを提供する必要があります。
  * RateVariationAcrossSites: 速度変動のモデル（オプション）

オプションの引数（デフォルト）：

  * `optimizeQ` (true): モデルの速度パラメータを固定するべきか、最適化するべきか？
  * `optimizeRVAS` (true): モデルはサイト間の速度の変動性のためのパラメータ（αおよび/またはp_invariable）を最適化するべきか？
  * `NLoptMethod` (`:LN_COBYLA`, 微分なし) 最適化アルゴリズムのため。その他のオプションについては、[NLopt](https://nlopt.readthedocs.io/en/latest/NLopt_Algorithms/)を参照してください。
  * 最適化が停止するタイミングを制御するための許容値：尤度に対する `ftolRel` (1e-12)、`ftolAbs` (1e-10)、およびモデルパラメータに対する `xtolRel` (1e-10)、`xtolAbs` (1e-10)。
  * サイト間の速度のガンマ分布のαパラメータの境界：`alphamin=0.05`、`alphamax=50`。
  * `verbose` (false): trueの場合、より多くの情報が出力されます。
  * `suppresswarnings` (false): trueの場合、[`check_matchtaxonnames!`](@ref)からの警告が抑制されます。

# 例：

```jldoctest fitDiscrete_block
julia> net = readnewick("(((A:2.0,(B:1.0)#H1:0.1::0.9):1.5,(C:0.6,#H1:1.0::0.1):1.0):0.5,D:2.0);");

julia> m1 = BinaryTraitSubstitutionModel([0.1, 0.1], ["lo", "hi"]);

julia> using DataFrames

julia> dat = DataFrame(species=["C","A","B","D"], trait=["hi","lo","lo","hi"]);

julia> fit1 = fitdiscrete(net, m1, dat)
PhyloTraits.StatisticalSubstitutionModel:
Binary Trait Substitution Model:
  rate lo→hi α=0.27222
  rate hi→lo β=0.34981
on a network with 1 reticulations
data:
  4 species
  1 trait
log-likelihood: -2.7277

julia> tips = Dict("A" => "lo", "B" => "lo", "C" => "hi", "D" => "hi");

julia> fit2 = fitdiscrete(net, m1, tips; xtolRel=1e-16, xtolAbs=1e-16, ftolRel=1e-16)
PhyloTraits.StatisticalSubstitutionModel:
Binary Trait Substitution Model:
  rate lo→hi α=0.27222
  rate hi→lo β=0.34981
on a network with 1 reticulations
data:
  4 species
  1 trait
log-likelihood: -2.7277
```

フィッティングされたオブジェクトにはネットワークのコピーが保存されますが、ネットワークの内部表現は `fit1.net` と元のネットワーク `net` で異なる場合があります：

```jldoctest fitDiscrete_block
julia> net = readnewick("(sp1:3.0,(sp2:2.0,(sp3:1.0,sp4:1.0):1.0):1.0);");

julia> using BioSymbols

julia> tips = Dict("sp1" => BioSymbols.DNA_A, "sp2" => BioSymbols.DNA_A, "sp3" => BioSymbols.DNA_G, "sp4" => BioSymbols.DNA_G);

julia> mJC69 = JC69([0.25], false);

julia> fitJC69 = fitdiscrete(net, mJC69, tips)
PhyloTraits.StatisticalSubstitutionModel:
Jukes and Cantor 69 Substitution Model,
  absolute rate version
  off-diagonal rates equal to 0.29233/3.
  rate matrix Q:
                 A       C       G       T
         A       *  0.0974  0.0974  0.0974
         C  0.0974       *  0.0974  0.0974
         G  0.0974  0.0974       *  0.0974
         T  0.0974  0.0974  0.0974       *
on a network with 0 reticulations
data:
  4 species
  1 trait
log-likelihood: -4.99274

julia> rv = RateVariationAcrossSites(alpha=1.0, ncat=4)
サイト間の速度の変動: 離散化されたガンマ
alpha: 1.0
ガンマの離散化のためのカテゴリ: 4
速度: [0.146, 0.513, 1.071, 2.27]

julia> fitdiscrete(net, mJC69, rv, tips; optimizeQ=false, optimizeRVAS=false)
PhyloTraits.StatisticalSubstitutionModel:
Jukes and Cantor 69 Substitution Model,
  absolute rate version
  off-diagonal rates equal to 0.25/3.
  rate matrix Q:
                 A       C       G       T
         A       *  0.0833  0.0833  0.0833
         C  0.0833       *  0.0833  0.0833
         G  0.0833  0.0833       *  0.0833
         T  0.0833  0.0833  0.0833       *
サイト間の速度の変動: 離散化されたガンマ
  alpha: 1.0
  ガンマの離散化のためのカテゴリ: 4
  速度: [0.146, 0.513, 1.071, 2.27]
on a network with 0 reticulations
data:
  4 species
  1 trait
log-likelihood: -5.2568

```

fixit: ユーザーが根の事前分布を指定できるオプションを追加します。特性モデルのために、等しい頻度または定常頻度のいずれかを使用します。 ```
