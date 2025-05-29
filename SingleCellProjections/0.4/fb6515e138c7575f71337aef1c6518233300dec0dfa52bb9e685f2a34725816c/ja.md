```
force_layout(data::DataMatrix;
             ndim=3,
             k,
             adj,
             kprojection=10,
             obs=:copy,
             adj_out,
             niter = 100,
             link_distance = 4,
             link_strength = 2,
             charge = 5,
             charge_min_distance = 1,
             theta = 0.9,
             center_strength = 0.05,
             velocity_decay = 0.9,
             initialAlpha = 1.0,
             finalAlpha = 1e-3,
             initialScale = 10,
             seed,
             rng)
```

`data`のためにフォースレイアウト（フォース指向k近傍グラフまたはSPRINGプロットとも呼ばれる）を計算します。通常、`data`は`svd`によって`10-100`次元に削減された後のDataMatrixです。

フォースレイアウトは、観測値がスプリングで接続され（接続された観測値が引き寄せられる）、一般的な「電荷」力がすべての観測値を互いに反発させ、中心力が観測値を原点の周りに保つ物理シミュレーションを実行することによって計算されます。この実装はd3-forceに基づいています: https://github.com/d3/d3-force、ライセンスについてはLICENSE.mdを参照してください。

`k`と`adj`のkwargsのうち、正確に1つが提供されなければなりません。詳細は以下を参照してください。

一般的なパラメータ:

  * `k` - 各観測値を接続する最近傍の数（以下の`adj`を計算します）。
  * `adj` - ブール値を持つ疎対称隣接行列。スプリングで接続されている場合は`true`、そうでない場合は`false`。
  * `kprojection` - 結果のフォースレイアウトに投影する際に使用される最近傍の数。（レイアウトの計算には使用されず、投影中のみ使用されます。）
  * `obs` - `:copy`（ソース`obs`のコピーを作成）または`:keep`（ソース`obs`オブジェクトを共有）を指定できます。
  * `adj_out` - オプションの`Ref`。指定された場合、（計算された）`adj`行列が`adj_out`に割り当てられます。

物理シミュレーションを制御するパラメータ:

  * `niter` - シミュレーションを実行する反復回数。
  * `link_distance` - 各スプリングの長さ。
  * `link_strength` - スプリング力の強さ。
  * `charge` - 電荷力の強さ。
  * `charge_min_distance` - 非常に近い観測値の電荷力を制限することによって数値的不安定性を回避するために使用されます。
  * `theta` - 電荷力のバーンズ-ハット近似における精度を制御するパラメータ。
  * `center_strength` - 中心力の強さ。
  * `velocity_decay` - 各反復で、観測値の現在の速度は`velocity_decay`で乗算されます。
  * `initialAlpha` - アルファ値は時間とともに減少し、初期に大きな変化を許可し、終わりに向かってより安定します。
  * `finalAlpha` - `initialAlpha`を参照してください。
  * `initialScale` - シミュレーションは、多変量ガウス分布から各観測値をランダムに描画することによって初期化され、`initialScale`でスケーリングされます。
  * `seed` - `rng`を初期化するために使用されるオプションのランダムシード。注意: これには`StableRNGs`パッケージをロードする必要があります。
  * `rng` - オプションのRNGオブジェクト。再現性に役立ちます。

# 例

```julia
julia> force_layout(data; ndim=3, k=100)
```
