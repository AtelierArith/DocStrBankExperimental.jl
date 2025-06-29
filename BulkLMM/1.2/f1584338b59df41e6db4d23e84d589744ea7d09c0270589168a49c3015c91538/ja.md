bulkscan(Y, G, K; optional inputs) bulkscan(Y, G, Z, K; optional inputs) - 追加の共変量 Z をモデル化する場合

複数の単変量特性と一連のゲノムマーカーに対するゲノムスキャンを実行します。

# 必須入力

  * `Y::Array{Float64, 2}`: 複数の (m) 特性の行列; 各列は特性 (次元: N*m)
  * `G::Array{Float64, 2}`: p のテストされたマーカーにおける遺伝子型確率の行列 (次元: N*p)
  * `K::Array{Float64, 2}`: N 人の被験者の遺伝的関連性行列 (次元:N*N)

# オプション入力

## 必須入力:

  * `addIntercept::Bool`: 設計行列に切片列を追加するオプション (デフォルト: true)
  * `reml::Bool`: 分散成分を推定するためのスキームのオプション (REML または ML による; デフォルト: false)
  * `method::String`: 使用される多重特性スキャンメソッドを示すキーワード引数; 現在サポートされているオプション: "null-grid" (最速、グリッドサーチ近似 Null-LMM)、"null-exact" (Null-LMM)、および "alt-grid" (グリッドサーチ近似 Exact-LMM)
  * `output_pvals::Bool`: LRT p値を追加で報告するオプション (デフォルト: false)

## 追加の共変量のモデル化:

  * `Z::AbstractArray{Float64, 2}`: 追加の非遺伝的共変量の行列 (テストされたマーカーに対して独立している必要があります)

## 選択したメソッドによる異なるオプション入力:

```
複数特性スキャンの場合、ユーザーは、より高い精度を得る必要があるか、短い時間を待つ必要があるかに応じて、3つのメソッドのいずれかを適用することを選択できます。許可される入力は選択によって異なります:
```

### グリッドサーチ近似法: "null-grid" (デフォルトメソッド) および "alt-grid"

  * `h2_grid::Array{Float64, 1}`: プロファイル尤度の最適化が行われる [0, 1) の h2 値のグリッド; グリッドが細かいほど精度が向上しますが、待機時間が長くなります。 (デフォルト: 0.0:0.10:0.90, 10 値)

### Null-LMM の正確な最適化 (ブレント法)、マルチスレッド: "null-exact"

  * `nb::Int64`: 特性の総数のサブグループの数; 各グループは独立して処理され、プロセスは並列化されます (デフォルト: 現在の Julia セッションのスレッド数)
  * `nt_blas::Int64`: BLAS ライブラリが使用するスレッドの数 (デフォルト: 1)

## パーミュテーションテスト:

```
現在、パーミュテーションテストは単一特性スキャンのみに対応しています。
```

## 重み付き残差分散の構造:

  * `weights::Array{Float64, 1}`: 特性の残差分散の不均等で重み付けされた構造をモデル化するためのオプションの重み (デフォルト: Missing、すなわち等しい残差分散)

## 数値技術 - 遺伝率最適化ステップを安定させるため

  * `optim_interval::Int64`: 遺伝率の区間 [0, 1) のサブ分割された領域の数; 各数値最適化スキーム (ブレント法) を実行する (デフォルト: 1、すなわち全体の区間)
  * `prior_variance::Float64`: 事前のスケールされた逆カイ二乗分布の残差分散のスケールパラメータ (デフォルト: 0)
  * `prior_sample_size::Float64`: 事前のスケールされた逆カイ二乗分布の残差分散の自由度パラメータ (デフォルト: 0)
  * `decomp_scheme::String`: 親族行列の分解スキームを示すキーワード; "eigen" または "svd" 分解のいずれか (デフォルト: "eigen")

# 戻り値:

単一特性スキャン関数の出力はオブジェクトです。ユーザーの入力とオプションに応じて、出力オブジェクトのフィールドは異なります。たとえば、`MT_out` という名前の戻り出力は "複数特性出力" として次のようになります:

## Null-LMM ("null-grid", "null-exact"):

  * `MT_out.h2_null_list::Array{Float64, 1}`: 各特性のために推定された h2_null のリスト
  * `MT_out.L::Array{Float64, 2}`: すべての入力特性の LOD スコアからなる 2 次元配列 (次元: p*m); 各列は1つの特性の LOD スコアを含みます

## Exact-LMM ("alt-grid"):

  * `MT_out.h2_panel::Array{Float64, 2}`: 各マーカーと各特性のために推定された h2 からなる 2 次元配列 (次元: p*m); 各列は1つの特性のための各マーカーに対して推定された h2 を含みます
  * `MT_out.L::Array{Float64, 2}`: すべての入力特性の LOD スコアからなる 2 次元配列 (次元: p*m); 各列は1つの特性の LOD スコアを含みます

## p値を報告するオプションがオンの場合、p値の結果は次のように返されます:

  * `MT_out.log10Pvals_mat::Array{Float64, 2}`: 各テスト (各特性と各マーカーの関連性) の -log10(p値) からなる 2 次元配列 (次元: p*m)
