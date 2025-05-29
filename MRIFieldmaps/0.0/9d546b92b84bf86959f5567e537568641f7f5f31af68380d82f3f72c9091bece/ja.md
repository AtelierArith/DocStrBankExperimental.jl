```
(fhat, times, out) = b0map(ydata, echotime; kwargs...)
```

複数の（`ne ≥ 2`）エコー時間画像からのフィールドマップ推定。前処理された非線形共役勾配法（NCG）を使用し、単調な線形探索を行います。このコードは任意の次元（2D、3Dなど）の画像と、複数のコイルで動作します。

注意：単一コイルデータはサイズを `(dims..., 1, ne)` に再形成する必要があります。

単一コイルの場合のコスト関数は次の通りです： `cost(w) = ∑_{j=1}^{#voxel} ∑_{m=1}^ne ∑_{n=1}^ne     |y_{mj} y_{nj}| wj (1 - cos(w_j * (t_m - t_n) + ∠y_{ni} - ∠y_{mj})) + R(w)` ここで `t_n` は `n` 番目のスキャンのエコー時間を示し、`R(w) = 0.5 * | C * w |^2` は1次または2次の有限差分に基づく二次的粗さ正則化項です。一般的なマルチコイルの場合のドキュメントを参照してください。

初期フィールドマップ `finit` と出力 `fhat` はHz単位のフィールドマップですが、内部的にはコードは `ω = 2π f`（rad/s）で動作します。

# 入力

  * `ydata (dims..., nc, ne)` `ne` セットの複素画像（`nc ≥ 1` コイル用）
  * `echotime::Echotime (ne ≥ 2)` エコー時間オフセット（秒単位）

# オプション

  * `finit (dims)` 初期フィールドマップ推定（Hz単位）；デフォルトは `b0init()` から
  * `smap (dims..., nc)` 複素コイルマップ；デフォルト `nothing`
  * `mask (dims...)` 論理再構成マスク；デフォルト: `trues(size(finit))`
  * `ninner` 単調線形探索の内部反復回数 デフォルト: `3` 内部反復
  * `b0init_args::NamedTuple = (;)` `b0init` のオプション、例えば `threshold`
  * `niter` 外部反復回数（デフォルト: `30`）
  * `order` 有限差分行列の次数（デフォルト: `2`）
  * `l2b` 正則化パラメータの `log2`（デフォルト: `-6`）
  * `gamma_type` CG方向：

      * `:PR` = Polak-Ribiere（デフォルト）
      * `:FR` = Fletcher-Reeves
  * `precon` 前処理器：

      * `:I`（なし）
      * `:diag`
      * `:chol` は多くのメモリを必要とする場合があります
      * `:ichol`（デフォルト）
  * `reset` 方向をリセットする前の反復回数（デフォルト: `Inf`）
  * `df` 水-脂肪画像におけるΔf値（デフォルト: `[0]`）単位Hz、例えば、3Tでの `[440]`
  * `relamp` マルチピーク水-脂肪における相対振幅（デフォルト: `[1]`）
  * `lldl_args::NamedTuple` `lldl` のオプション、デフォルト: `(;memory=2)`
  * `track::Bool` `true` の場合、コストを追跡し、すべての反復を保存（デフォルト: `false`）
  * `chat::Bool = true` # 各反復で `@info` を更新
  * `chat_iter::Int = 10` # 数回の反復ごとに進捗報告を印刷。

# 出力

  * `fhat` Hz単位の最終フィールドマップ推定
  * `times (niter+1)` 各反復の壁時間
  * `out::NamedTuple` が含まれる：

      * `(xw, xf) (dims)` 水/脂肪画像（`!iszero(df)` の場合）
      * `finit (dims)` 初期フィールドマップ
  * `track == true` の場合、`out` には次も含まれます：

      * `costs (niter+1)` （非凸）各反復のコスト
      * `fhats (dims, niter+1)` 各反復のフィールドマップ推定

このアルゴリズムは次の論文に基づいています：C Y Lin, J A Fessler, "Efficient Regularized Field Map Estimation in 3D MRI", IEEE TCI 2020 https://doi.org/10.1109/TCI.2020.3031082 https://arxiv.org/abs/2005.08661

このコードを使用する場合は、その論文を引用してください。
