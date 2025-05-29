```julia
mutable struct Shrink <: Conditioner
        metric 
        radius 
        refpoint 
        reshape 
        epsilon 
        verbose 
        threaded 
        ## Fitted parameters
        γ 
        m 
        sd 
```

**測地線収縮**コンディショナーの可変構造体。

正定値行列の多様体における点の集合$𝐏$が与えられたとき、このコンディショナーは指定された`metric`に従って定義された多様体上の測地線に沿ってすべての点を単位行列$I$に向かって移動させます。これにより、$I$を中心とした球が効果的に定義されます。

$$
I
$$

から$𝐏$の各点$P$への測地線のステップサイズ$γ$は次のように与えられます。

$$
\gamma=\frac{r\sqrt{n}}{δ(P, I) + ϵ}
$$

ここで、$r$は`radius`引数、$n$は$P$の次元、$δ(P, I)$は指定された`metric`に従った$P$のノルム、$ϵ$は引数`epsilon`として与えられるオプションの小さな正の数です。

このコンディショナーには、構築時に渡すことができるキーワード引数でもある以下のフィールドがあります。

`.metric`は、デフォルトが`PosDefManifold.Euclidean`の[Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1)型です。

収縮後、点の集合$𝐏$は求められた`.radius`を取得します。これはコンストラクタにオプションのキーワード引数として与えられます（デフォルト: 0.02）。これは、単位行列からの取得した距離（ノルム）の尺度であり、具体的には、`.refpoint`=:maxの場合は最大距離、または`.refpoint`=:mean（デフォルト）の場合は平均偏心率です。最初のケースでは、引数`radius`はすべての点を制限する球を定義し、半径は変換された点の単位行列からの最大距離+ $ϵ$に等しくなります。第二のケースでは、球の実際の半径は次のようになります。

$$
\sqrt{\frac{1}{n}\sum_{j=1}^{k}δ(P_j, I) + ϵ}
$$

。

`.reshape`は、収縮後に集合$𝐏$の固有値を再形成するためのブール値です。これはフィッシャー（アフィン不変）メトリックにのみ適用されます。デフォルト: false。以下を参照してください。

`.epsilon`は、上記の$ϵ$である非負の実数です。デフォルト: 0.0。

`.verbose`はブール値です。trueの場合、情報がREPLに出力されます。デフォルト: false。

`.threaded`はマルチスレッドを使用するためのブール値です。デフォルト: true。

インスタンスを構築するために、`metric`は引数であり、`radius`、`refpoint`、`reshape`、`epsilon`、`verbose`、および`threaded`はオプションのキーワード引数です。

**フィッティングされたパラメータ**

コンディショナーがフィッティングされると、次のフィールドが書き込まれます。

`.γ`は、$I$から$𝐏$の各行列への測地線のステップサイズ（`metric`に従う）です。

`.m`と`.sd`は、収縮後の集合の固有値の平均と標準偏差です。これは、フィッシャーメトリックが採用されている場合にのみ適用される再形成に使用されます。再形成は、入力セットが再中心化されている場合にのみ意味があります（[`Recenter`](@ref）を参照）。これは、収縮後に集合の固有値を再中心化し（平均 = 1）、標準偏差が`.radius`に等しくなるように正規化します。

**例**:

```julia
using PosDefManifoldML, PosDefManifold

# フィッシャーメトリックを採用し、再形成を使用するコンディショナーを作成
S = Shrink(PosDefManifold.Fisher; reshape = true)
```

**関連項目**: [`fit!`](@ref), [`transform!`](@ref), [`crval`](@ref)
