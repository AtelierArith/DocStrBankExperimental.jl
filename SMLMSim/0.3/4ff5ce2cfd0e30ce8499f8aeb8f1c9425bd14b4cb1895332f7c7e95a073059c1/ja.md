# SMLMSim.jl API 概要

SMLMSimは、現実的な物理特性を持つ単一分子局在顕微鏡（SMLM）データをシミュレーションするためのJuliaパッケージです。静的SMLMシミュレーション、拡散相互作用シミュレーション、および顕微鏡画像生成のためのツールを提供します。

## 主要概念

### 物理単位

すべてのシミュレーションは一貫した物理単位を使用します：

  * 空間次元：マイクロメートル（μm）
  * 時間：秒（s）
  * 拡散係数：μm²/s
  * 反応速度定数：s⁻¹

### コアコンポーネント

  * **パターン**：分子の空間的配置（例：オリゴマー、ライン）
  * **分子**：状態遷移を持つ蛍光体の光物理モデル
  * **シミュレーション**：異なるシミュレーションタイプのためのパラメータと関数
  * **ノイズ**：光子統計に基づく現実的な局在不確実性
  * **カメラ画像**：シミュレーションデータからの顕微鏡画像の生成

## 型階層

  * `AbstractSim`：すべてのシミュレーションタイプのベース型

      * `SMLMSimParams`：シミュレーションパラメータのベース型

          * `StaticSMLMParams`：静的SMLMシミュレーションのためのパラメータ
          * `DiffusionSMLMParams`：拡散シミュレーションのためのパラメータ
  * `Pattern`：すべての分子パターンのベース型

      * `Pattern2D`：2Dパターンのベース型

          * `Nmer2D`：円形に配置されたN分子
          * `Line2D`：直線に沿って配置された分子
      * `Pattern3D`：3Dパターンのベース型

          * `Nmer3D`：3Dで円形に配置されたN分子
          * `Line3D`：3Dの直線に沿って配置された分子
  * `Molecule`：すべての光物理モデルのベース型

      * `GenericFluor`：運動状態モデルを持つ一般的な蛍光体
  * `AbstractDiffusingEmitter`：拡散するエミッターのベース型

      * `DiffusingEmitter2D`：拡散状態を持つ2Dエミッター
      * `DiffusingEmitter3D`：拡散状態を持つ3Dエミッター

## 必須タイプ

### StaticSMLMParams

固定された分子パターンを持つ静的SMLMシミュレーションのためのパラメータ。

```julia
Base.@kwdef mutable struct StaticSMLMParams <: SMLMSimParams
    density::Float64 = 1.0          # 粒子あたりの密度（μm²あたり）
    σ_psf::Float64 = 0.13           # PSF幅（マイクロメートル）
    minphotons::Int = 50            # 検出のための最小光子数
    ndatasets::Int = 10             # シミュレーションするデータセットの数
    nframes::Int = 1000             # データセットあたりのフレーム数
    framerate::Float64 = 50.0       # 秒あたりのフレーム数
    ndims::Int = 2                  # 次元数（2または3）
    zrange::Vector{Float64} = [-1.0, 1.0]  # 3Dシミュレーションのための軸方向範囲 [min_z, max_z]
end
```

### DiffusionSMLMParams

Smoluchowskiダイナミクスを使用した拡散ベースのSMLMシミュレーションのためのパラメータ。

```julia
Base.@kwdef mutable struct DiffusionSMLMParams <: SMLMSimParams
    density::Float64 = 1.0          # 数密度（分子/μm²）
    box_size::Float64 = 10.0        # シミュレーションボックスのサイズ（μm）
    diff_monomer::Float64 = 0.1     # モノマーの拡散係数（μm²/s）
    diff_dimer::Float64 = 0.05      # ダイマーの拡散係数（μm²/s）
    diff_dimer_rot::Float64 = 0.5   # ダイマーの回転拡散係数（rad²/s）
    k_off::Float64 = 0.2            # ダイマーの解離速度（s⁻¹）
    r_react::Float64 = 0.01         # 反応半径（μm）
    d_dimer::Float64 = 0.05         # ダイマー内のモノマーの分離（μm）
    dt::Float64 = 0.01              # 時間ステップ（s）
    t_max::Float64 = 10.0           # 総シミュレーション時間（s）
    ndims::Int = 2                  # 次元数（2または3）
    boundary::String = "periodic"   # 境界条件のタイプ（"periodic"または"reflecting"）
    camera_framerate::Float64 = 10.0 # カメラのフレーム数（Hz）
    camera_exposure::Float64 = 0.1   # フレームあたりのカメラ露光時間（s）
end
```

### 分子パターン

#### Nmer2D

直径dの円の周りに対称的に配置されたN分子。

```julia
mutable struct Nmer2D <: Pattern2D
    n::Int               # パターン内の分子の数
    d::Float64           # 円の直径（マイクロメートル）
    x::Vector{Float64}   # マイクロメートル単位の分子のX位置
    y::Vector{Float64}   # マイクロメートル単位の分子のY位置
end
```

#### Line2D

2つの端点の間に均一にランダムに分布した点。

```julia
mutable struct Line2D <: Pattern2D
    n::Int                # パターン内の分子の数
    x::Vector{Float64}    # マイクロメートル単位の分子のX位置
    y::Vector{Float64}    # マイクロメートル単位の分子のY位置
    λ::Float64            # 線形分子密度（分子/マイクロメートル）
    endpoints::Vector{Tuple{Float64,Float64}}  # 端点座標のベクトル
end
```

### 蛍光体モデル

#### GenericFluor

光物理特性を持つ蛍光体を定義します。

```julia
struct GenericFluor <: Molecule
    γ::AbstractFloat     # 光子放出率（Hz）
    q::Array{<:AbstractFloat}  # 状態遷移のための速度行列
end
```

## コンストラクタの例

### シミュレーションパラメータの作成

```julia
# デフォルトパラメータを使用した静的SMLM
params_static = StaticSMLMParams()

# 静的シミュレーションのためのカスタムパラメータ
params_static = StaticSMLMParams(
    density = 2.0,        # 2パターン/μm²
    σ_psf = 0.15,         # 150nm PSF幅
    nframes = 2000,       # 2000フレーム
    framerate = 20.0      # 20 fps
)

# デフォルトパラメータを使用した拡散シミュレーション
params_diff = DiffusionSMLMParams()

# 拡散シミュレーションのためのカスタムパラメータ
params_diff = DiffusionSMLMParams(
    density = 0.5,        # μm²あたりの分子数
    box_size = 15.0,      # 15μmのボックスサイズ
    diff_monomer = 0.2,   # 0.2 μm²/sの拡散係数
    k_off = 0.1,          # 0.1 s⁻¹の解離速度
    t_max = 20.0          # 20sのシミュレーション時間
)
```

### パターンの作成

```julia
# 100nmの直径を持つ8分子パターンを作成（デフォルト）
nmer = Nmer2D()

# 6分子と200nmの直径を持つカスタムパターンを作成
hexamer = Nmer2D(n=6, d=0.2)  # dはマイクロメートル単位

# 3Dパターンを作成
octamer3d = Nmer3D(n=8, d=0.15)

# ラインパターンを作成
line = Line2D(λ=5.0, endpoints=[(-2.0, 0.0), (2.0, 0.0)])  # 5分子/μm

# 3Dラインパターンを作成
line3d = Line3D(λ=8.0, endpoints=[(-1.0, 0.0, -0.5), (1.0, 0.0, 0.5)])
```

### 蛍光体モデルの作成

```julia
# デフォルトパラメータを持つ蛍光体を作成
fluor = GenericFluor()

# カスタムパラメータを持つ蛍光体を作成
# γ=10,000光子/s, k_off=10 Hz, k_on=0.1 Hz
fluor = GenericFluor(1e4, [-10.0 10.0; 0.1 -0.1])

# 2状態キーワードコンストラクタを使用して蛍光体を作成
fluor = GenericFluor(photons=1e4, k_off=5.0, k_on=0.5)
```

### カメラの作成

```julia
# 100nmのピクセルを持つカメラを作成（128x128ピクセル）
camera = IdealCamera(128, 128, 0.1)  # 128×128ピクセル、100nmピクセル

# ピクセルエッジの配列を使用して視野を指定
pixel_edges_x = 0.0:0.1:12.8  # 0から12.8μmまで0.1μm刻み
pixel_edges_y = 0.0:0.1:12.8
camera = IdealCamera(pixel_edges_x, pixel_edges_y)
```

## コア関数

### シミュレーション

#### simulate

異なるシミュレーションタイプのための複数のメソッドを持つメインシミュレーション関数。

```julia
# 静的SMLMシミュレーション
# まずシミュレーションパラメータを作成
params = StaticSMLMParams()

# 次にシミュレーションを実行
smld_true, smld_model, smld_noisy = simulate(
    params;
    pattern=Nmer2D(),
    molecule=GenericFluor(),
    camera=IdealCamera(128, 128, 0.1)
)

# 拡散シミュレーション
# まずシミュレーションパラメータを作成
params_diff = DiffusionSMLMParams()

# 次にシミュレーションを実行
smld = simulate(
    params_diff;
    photons=1000.0
)
```

#### kinetic_model

既存の局在データから運動的な点滅モデルを生成します。

```julia
# kinetic_modelの呼び出し例
# まず必要な入力を作成または取得
smld_true = ... # 真の位置を持つBasicSMLD
fluor = GenericFluor(1e4, [-10.0 10.0; 0.5 -0.5])  # 蛍光体モデル
nframes = 1000    # フレーム数
framerate = 50.0  # 秒あたりのフレーム数

# 関数を呼び出す
smld_model = kinetic_model(
    smld_true,     # エミッター位置を持つBasicSMLD
    fluor,         # 運動率を持つ分子
    nframes,       # フレーム数
    framerate;     # 秒あたりのフレーム数
    ndatasets=1,   # 独立したデータセットの数
    minphotons=50.0, # 検出のための最小光子数
    state1=:equilibrium  # 初期状態のサンプリング
)
```

#### apply_noise

光子数に基づいてエミッター位置に局在不確実性を追加します。

```julia
# apply_noiseの使用例

# まず、前のステップからsmld_modelが必要です
# 例えば、kinetic_model()の出力から

# 2Dエミッターの場合 - 130nm PSF幅でノイズを追加
smld_noisy = apply_noise(smld_model, 0.13)  # 0.13 μm = 130nm PSF幅

# 3Dエミッターの場合 - 各次元でPSF幅を指定
smld_noisy_3d = apply_noise(smld_model_3d, [0.13, 0.13, 0.39])  # [x, y, z]の幅（μm単位）
```

### 画像生成

#### gen_images

指定されたPSFモデルを使用してSMLDデータからカメラ画像を生成します。

```julia
images = gen_images(
    smld::SMLD,
    psf::AbstractPSF;
    dataset::Int=1,                # SMLDから使用するデータセット番号
    frames=nothing,                # 生成する特定のフレーム（デフォルト：すべてのフレーム）
    support=Inf,                   # PSFサポート領域のサイズ（詳細は以下を参照）
    sampling=2,                    # PSF統合のためのスーパサンプリング係数
    threaded=true,                 # マルチスレッドを有効にする
    bg=0.0,                        # 背景信号レベル（ピクセルあたりの光子数）
    poisson_noise=false,           # ポアソンノイズを適用
    camera_noise=false             # カメラ読み出しノイズを適用
)

# supportパラメータはPSF計算領域を制御します：
# 1. Inf（デフォルト）：画像全体にわたってPSFを計算（最も正確ですが最も遅い）
support=Inf

# 2. 実数：各エミッターの周りに与えられた半径の円形領域を使用
# 通常、PSF幅の3〜5倍が精度に対して十分で、パフォーマンスが向上します
support=1.0  # 各エミッターの周りの1.0 µm半径

# 3. タプル（xmin, xmax, ymin, ymax）：マイクロメートル単位の明示的な領域
support=(4.0, 6.0, 4.0, 6.0)  # この領域内でのみPSFを計算
```

#### gen_image

単一フレームのカメラ画像を生成します。

```julia
# 単一フレーム画像を生成する例

# まず、変数を定義
smld = ... # あなたのSMLDデータ
psf = GaussianPSF(0.15)  # 150nm幅のPSFモデル
frame_number = 10  # 生成したいフレーム

# 特定のフレームの画像を生成
single_frame = gen_image(
    smld,          # SMLDデータ 
    psf,           # PSFモデル
    frame_number;  # 生成するフレーム
    support=1.0,   # gen_imagesと同じキーワード引数
    bg=5.0,
    poisson_noise=true
)
```

### 分析関数

#### 拡散分析

```julia
# 拡散分析関数の使用例

# まず、拡散シミュレーションを実行
params = DiffusionSMLMParams()
smld = simulate(params)

# 拡散シミュレーションからダイマーを抽出
dimer_smld = get_dimers(smld)

# モノマーを抽出
monomer_smld = get_monomers(smld)

# 時間に対するダイマー形成を分析
frames, fractions = analyze_dimer_fraction(smld)

# 平均ダイマー寿命を分析
lifetime = analyze_dimer_lifetime(smld)

# 時間に対する状態変化を追跡
state_history = track_state_changes(smld)
```

#### トラッキングユーティリティ

```julia
# トラッキングユーティリティの使用例

# まず、シミュレーションを実行
params = StaticSMLMParams()
smld_true, smld_model, smld_noisy = simulate(params)

# 抽出するトラックIDを指定
track_id = 1  # 抽出するトラックのID

# IDによって特定のトラックを取得
track_smld = get_track(smld_noisy, track_id)

# ユニークなトラックの数を取得
n_tracks = get_num_tracks(smld_noisy)

# すべてのトラックを別々のSMLDとして取得
track_smlds = get_tracks(smld_noisy)
```

### パターン操作

```julia
# パターン操作の使用例

# パターンを作成
pattern2d = Nmer2D(n=6, d=0.2)
pattern3d = Nmer3D(n=8, d=0.15)

# 2Dパターンを45度回転
rotate!(pattern2d, π/4) 

# オイラー角（ZYZ規則）で3Dパターンを回転
rotate!(pattern3d, π/4, π/6, π/3)  # α, β, γ角

# 回転行列を使用して3Dパターンを回転
θ = π/2 # 90度
R = [cos(θ) -sin(θ) 0; sin(θ) cos(θ) 0; 0 0 1]  # Z軸回転
rotate!(pattern3d, R)

# フィールド内のランダムパターン分布を生成
field_x = 10.0 # μm
field_y = 10.0 # μm
density = 1.0  # μm²あたりのパターン数

# 2D分布の座標を取得
x, y = uniform2D(density, pattern2d, field_x, field_y)

# 3D分布の座標を取得
x, y, z = uniform3D(density, pattern3d, field_x, field_y, zrange=[-2.0, 2.0])
```

## 一般的なワークフロー

### 静的SMLMシミュレーションワークフロー

1. シミュレーションパラメータを定義
2. パターンを作成（またはデフォルトを使用）
3. 蛍光体モデルを定義（またはデフォルトを使用）
4. シミュレーションを実行して真の位置、運動モデル、およびノイズのある局在を取得
5. 顕微鏡画像を生成するか、データを分析

```julia
# 1. パラメータを定義
params = StaticSMLMParams(
    density = 1.0,
    σ_psf = 0.13,
    nframes = 1000
)

# 2. パターンを作成
pattern = Nmer2D(n=6, d=0.2)  # 200nmの直径を持つヘキサマー

# 3. 蛍光体モデルを定義
fluor = GenericFluor(photons=1e4, k_off=10.0, k_on=0.5)

# 4. シミュレーションを実行
smld_true, smld_model, smld_noisy = simulate(
    params;
    pattern=pattern,
    molecule=fluor
)

# 5. 効率的なPSFサポートを使用して顕微鏡画像を作成
psf = GaussianPSF(0.15)  # 150nm PSF幅
images = gen_images(smld_model, psf; 
    support=1.0,         # 各エミッターの周りの1.0 μm半径
    poisson_noise=true   # 現実的な光子カウントノイズを追加
)
```

### 拡散シミュレーションワークフロー

1. 拡散パラメータを定義
2. シミュレーションを実行してエミッターの軌跡を取得
3. 拡散および相互作用のダイナミクスを分析
4. 顕微鏡画像を生成

```julia
# 1. パラメータを定義
params = DiffusionSMLMParams(
    density = 0.5,        # μm²あたりの分子数
    box_size = 10.0,      # μm
    diff_monomer = 0.1,   # μm²/s
    diff_dimer = 0.05,    # μm²/s
    k_off = 0.2,          # s⁻¹
    t_max = 10.0          # s
)

# 2. シミュレーションを実行
smld = simulate(params)

# 3. 結果を分析
dimer_smld = get_dimers(smld)
frames, fractions = analyze_dimer_fraction(smld)

# 4. 有限PSFサポートを持つ顕微鏡画像を生成
psf = GaussianPSF(0.15)  # 150nm PSF幅
images = gen_images(smld, psf; 
    support=1.0,         # 1.0 μm PSFサポート半径（より速い）
    bg=5.0,              # ピクセルあたりの背景光子数
    poisson_noise=true   # 現実的な光子カウントノイズを追加
)
```

## 完全な例

### 静的SMLMと画像生成

```julia
using SMLMSim
using MicroscopePSFs

# カメラとシミュレーションパラメータを定義
camera = IdealCamera(128, 128, 0.1)  # 128×128ピクセル、100nmピクセル
params = StaticSMLMParams(density=1.0, σ_psf=0.13, nframes=1000) 

# 8分子リングパターンのシミュレーションを実行
smld_true, smld_model, smld_noisy = simulate(
    params;
    pattern=Nmer2D(n=8, d=0.1),  # 100nmの直径のリング
    molecule=GenericFluor(1e4, [-10.0 10.0; 0.5 -0.5]),  # γ=10,000, k_off=10, k_on=0.5
    camera=camera
)

# PSFモデルを作成
psf = GaussianPSF(0.15)  # 150nm PSF幅

# 有限PSFサポートを持つ顕微鏡画像を生成
images = gen_images(smld_model, psf;
    support=1.0,         # 1.0 μm PSFサポート半径（Infより速い）
    bg=5.0,              # ピクセルあたり5の背景光子
    poisson_noise=true   # 現実的な光子カウントノイズを追加
)

println("生成された局在は $(length(smld_noisy.emitters)) で、画像は $(size(images,3)) です。")
```

### 拡散とダイマー分析

```julia
using SMLMSim
using MicroscopePSFs

# 拡散シミュレーションパラメータを設定
params = DiffusionSMLMParams(
    density = 0.5,        # μm²あたりの分子数
    box_size = 10.0,      # μm
    diff_monomer = 0.1,   # μm²/s
    diff_dimer = 0.05,    # μm²/s
    k_off = 0.2,          # s⁻¹
    t_max = 10.0,         # s
    boundary = "reflecting"  # 反射境界を使用
)

# 拡散シミュレーションを実行
smld = simulate(params)

# ダイマー形成を分析
frames, dimer_fraction = analyze_dimer_fraction(smld)
avg_lifetime = analyze_dimer_lifetime(smld)

# 有限PSFサポートを持つ顕微鏡画像を生成
psf = GaussianPSF(0.15)  # 150nm PSF幅
images = gen_images(smld, psf; 
    support=1.0,         # 1.0 μm PSFサポート半径（より速い）
    bg=2.0,              # ピクセルあたりの背景光子数
    poisson_noise=true   # 現実的な光子カウントノイズを追加
)

println("シミュレーションが完了し、エミッターは $(length(smld.emitters)) です")
println("平均ダイマー比率: $(mean(dimer_fraction))")
println("平均ダイマー寿命: $(avg_lifetime) 秒")
```

### カスタムパターンを使用した3Dシミュレーション

```julia
using SMLMSim
using MicroscopePSFs

# 2つのリングを異なるz位置に持つカスタム3Dパターンを定義
mutable struct DoubleRing3D <: Pattern3D
    n::Int
    d1::Float64
    d2::Float64
    z1::Float64
    z2::Float64
    x::Vector{Float64}
    y::Vector{Float64}
    z::Vector{Float64}
end

function DoubleRing3D(; n=8, d1=0.1, d2=0.2, z1=-0.2, z2=0.2)
    total_n = 2*n
    x = zeros(total_n)
    y = zeros(total_n)
    z = zeros(total_n)
    
    # 最初のリング（下）
    for i = 1:n
        θ = 2π * (i-1) / n
        x[i] = d1/2 * cos(θ)
        y[i] = d1/2 * sin(θ)
        z[i] = z1
    end
    
    # 2番目のリング（上）
    for i = 1:n
        θ = 2π * (i-1) / n + π/n  # 2番目のリングのオフセット角
        x[n+i] = d2/2 * cos(θ)
        y[n+i] = d2/2 * sin(θ)
        z[n+i] = z2
    end
    
    return DoubleRing3D(n, d1, d2, z1, z2, x, y, z)
end

# カメラとパラメータを作成
camera = IdealCamera(128, 128, 0.1)
params = StaticSMLMParams(
    density = 0.5,
    σ_psf = 0.13,
    nframes = 2000,
    ndims = 3,
    zrange = [-1.0, 1.0]
)

# カスタムパターンを作成
double_ring = DoubleRing3D(n=6, d1=0.15, d2=0.3, z1=-0.3, z2=0.3)

# シミュレーションを実行
smld_true, smld_model, smld_noisy = simulate(
    params;
    pattern=double_ring,
    camera=camera
)

# 3DアスティグマティックPSFを使用して有限サポートで画像を生成
# ゼルニケ係数を使用してアスティグマティズムを持つPSFを作成
using MicroscopePSFs
zc = ZernikeCoefficients(15)
zc.phase[6] = 0.5  # 垂直アスティグマティズムを追加
psf_scalar = ScalarPSF(1.4, 0.532, 1.52; zernike_coeffs=zc)

# スピードのためにSplinePSFを作成
xy_sampling, z_sampling = 0.05, 0.1
x_range = y_range = -1.0:xy_sampling:1.0
z_range = -1.0:z_sampling:1.0
psf_spline = SplinePSF(psf_scalar, x_range, y_range, z_range)

# スプラインPSFを使用して有限サポートで画像を生成
images = gen_images(smld_model, psf_spline; 
    support=0.5,         # 0.5 μm PSFサポート半径（パフォーマンス向上）
    bg=5.0,              # ピクセルあたりの背景光子
    poisson_noise=true   # 現実的な光子カウントノイズを追加
)

println("3Dで $(length(smld_noisy.emitters)) 局在が生成されました")
```
