```
SMLMSim
```

SMLMSim.jlパッケージのメインモジュール。

# API概要

APIの包括的な概要については、`api_overview`のヘルプモードを使用してください：

```
?api_overview
```

または、プログラム的に完全なAPIドキュメントにアクセスします：

```
docs = SMLMSim.api_overview()
```

このパッケージは、単一分子局在顕微鏡（SMLM）データのシミュレーションのためのツールを提供します。以下のモジュールが含まれています：

  * **Core:** 基本的なタイプ（分子、パターン）と光物理シミュレーション（CTMC、点滅）。
  * **StaticSMLM:** 点滅と局在ノイズを伴う静的エミッタのシミュレーション。
  * **InteractionDiffusion:** Smoluchowskiダイナミクスを使用して、拡散および相互作用するエミッタ（例：二量体化）のシミュレーション。
  * **CameraImages:** エミッタデータからのシミュレートされたカメラ画像の生成、ノイズモデルを含む。

メインの`SMLMSim`モジュールは、これらのサブモジュールからの主要なタイプと関数を再エクスポートし、統一されたユーザーインターフェースを提供します。

# 使用法

```julia
using SMLMSim

# 例：静的シミュレーション
params_static = StaticSMLMParams(density=1.0, σ_psf=0.13)
_, _, smld_noisy = simulate(params_static)

# 例：拡散シミュレーション
params_diff = DiffusionSMLMParams(density=0.5, diff_monomer=0.1)
smld_diff = simulate(params_diff)

# 例：画像の生成
psf = GaussianPSF(0.15)
images = gen_images(smld_noisy, psf)
```
