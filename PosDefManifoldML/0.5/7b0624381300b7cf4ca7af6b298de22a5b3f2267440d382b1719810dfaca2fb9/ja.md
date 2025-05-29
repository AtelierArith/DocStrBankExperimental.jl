```julia
function tsMap(	metric :: Metric, 𝐏 :: ℍVector;
    w           :: Vector = Float64[],
    ✓w         :: Bool = true,
    ⏩          :: Bool = true,
    meanISR     :: Union{ℍ, Nothing, UniformScaling}  = nothing,
    meanInit    :: Union{ℍ, Nothing}  = nothing,
    tol         :: Real = 0.,
    transpose   :: Bool = true,
    vecRange    :: UnitRange = 1:size(𝐏[1], 1))
```

正定行列 $P_i$ の [接空間マッピング](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.logMap) は、平均 *G* とともに、これらの点が単位行列に平行移動された後に次のように与えられます：

$$
S_i=\textrm{log}(G^{-1/2} P_i G^{-1/2})
$$

。

julia によって `Hermitian` としてフラグ付けされた *k* 行列のベクトル `𝐏` が与えられた場合、[vecP](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.vecP) 操作に従って、行列 `𝐏` の接ベクトルをベクトル化した行列 *X* を返します。

行列 `𝐏` の平均 *G* は、[Metric](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#Metric::Enumerated-type-1) 型の指定された `metric` に従って求められます。自然な選択は [フィッシャー計量](https://marco-congedo.github.io/PosDefManifold.jl/dev/introToRiemannianGeometry/#Fisher-1) です。計量がフィッシャー、logdet0、またはワッサースタインの場合、平均はオプションのキーワード引数 `tol` で与えられた許容誤差を持つ反復アルゴリズムで求められます。デフォルトでは、`tol` は関数 [mean](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#Statistics.mean) によって設定されます。これらの反復アルゴリズムには、オプションのキーワード引数 `meanInit` によって、エルミート行列として特定の初期化を提供できます。

任意の計量に対して、重み付き平均 *G* を計算するために、*k* のオプションの非負の重み `w` を提供できます。`w` が空でなく、オプションのキーワード引数 `✓w` が true（デフォルト）である場合、重みは合計が 1 になるように正規化されます。そうでない場合、重みは渡された通りに使用され、すでに正規化されている必要があります。このオプションは、同じ重みベクトルを毎回正規化することなく、この関数を繰り返し呼び出すことを可能にするために提供されています。

オプションのキーワード引数 `meanISR` としてエルミート行列が提供されると、平均 *G* は計算されず、この行列が逆平方根 (ISR) $G^{-1/2}$ として式に直接使用されます。`meanISR` が提供されると、引数 `tol` と `meanInit` はまったく効果がありません。

`meanISR=I` が使用されると、接空間マッピングは単位行列で次のように得られます：

$$
S_i=\textrm{log}(P_i)
$$

。

これは、ログユークリッド計量を採用した接空間マッピングに対応します。また、データがすでに再中心化されている場合（例えば、[`Recenter`](@ref) 前処理器を使用して）にも便利です。`meanISR=I` が使用されると、引数 `w`、`✓w`、`meanInit`、および `tol` は無視されます。

`meanISR` が提供されない場合、2-タプル $(X, G^{-1/2})$ を返します。それ以外の場合は、行列 *X* のみを返します。

オプションのキーワード引数 `vecRange` として `UnitRange` が提供されると、ベクトル化は指定された範囲の行列 `𝐏` の列（または行）のみを対象とします。

オプションのキーワード引数 `transpose` が true（デフォルト）の場合、*X* はその行に *k* のベクトル化された接ベクトルを保持し、そうでない場合はその列に配置されます。前者の場合の行の次元と後者の場合の列の次元は *n(n+1)÷2*（整数除算）であり、ここで *n* は `𝐏` の行列のサイズです。ただし、`𝐏` の行列の列または行のサブセットをカバーする `vecRange` が提供されている場合、次元は小さくなります。（[vecP](https://marco-congedo.github.io/PosDefManifold.jl/dev/riemannianGeometry/#PosDefManifold.vecP) を参照）。

オプションのキーワード引数 `⏩` が true（デフォルト）の場合、平均の計算と接空間への射影はマルチスレッドで行われます。Julia に指示されたスレッド数が *<2* または *<2k* の場合、マルチスレッドは自動的に無効になります。

**例**：

```julia
using PosDefManifoldML

# 4つのランダムな対称正定行列 3x3 を生成
Pset = randP(3, 4)

# 接空間で投影し、ベクトル化する
X, G⁻½ = tsMap(Fisher, Pset)

# X は 4x6 行列で、6 は
# ベクトル化された接ベクトルのサイズ（n=3, n*(n+1)/2=6）

# 繰り返し呼び出す必要がある場合、Pset の行列の逆平方根を提供することで
# より高速な計算が得られます、例えば、
X1 = tsMap(Fisher, ℍVector(Pset[1:2]); meanISR = G⁻½)
X2 = tsMap(Fisher, ℍVector(Pset[3:4]); meanISR = G⁻½)
```

**参照**: [ℍVector 型](https://marco-congedo.github.io/PosDefManifold.jl/dev/MainModule/#%E2%84%8DVector-type-1)。
