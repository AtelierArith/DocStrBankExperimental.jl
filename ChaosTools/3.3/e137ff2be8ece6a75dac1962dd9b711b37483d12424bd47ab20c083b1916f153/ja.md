```
lyapunovspectrum(ds::DynamicalSystem, N, k = dimension(ds); kwargs...) -> λs
```

`ds`のリャプノフ指数のスペクトルを計算します[^Lyapunov1992]。これは、偏差ベクトルによって定義された平行六面体にQR分解を適用することによって行われ、合計で`N`の進化ステップを経ます。スペクトルは最大から最小にソートされて返されます。第三引数`k`はオプションで、計算するリャプノフ指数の数を指定します（デフォルトは`dimension(ds)`です）。

関連情報としては、[`lyapunov`](@ref)、[`local_growth_rates`](@ref)があります。

**注意:** この関数は単に[`TangentDynamicalSystem`](@ref)を初期化し、以下のメソッドを呼び出します。これは、デフォルトで自動ヤコビアンが使用されることを意味します。手動でヤコビアンをコーディングした場合は、手動で[`TangentDynamicalSystem`](@ref)を初期化してください。

## キーワード引数

  * `u0 = current_state(ds)`: 開始する状態。
  * `Ttr = 0`: アルゴリズムの適用前にシステムを進化させるための追加の過渡時間。離散システムの場合は`Int`である必要があります。システムと偏差ベクトルの両方がこの時間進化します。
  * `Δt = 1`: 連続直交化ステップ間の個々の進化の時間。連続システムの場合、これは近似値です。
  * `show_progress = false`: プロセスの進行状況を示すプログレスバーを表示します。

## 説明

私たちが採用するメソッドは、[ ^Geist1990]の"H2"であり、元々は[ ^Benettin1980]で述べられ、[ ^DatserisParlitz2022]で教育的な形で説明されています。

接線空間における`D`次元の平行六面体を定義する偏差ベクトルは、システムの接線力学を使用して進化します（[`TangentDynamicalSystem`](@ref)を参照）。各ステップでのQR分解は、平行六面体の各次元の局所成長率を提供します。各ステップで平行六面体は直交化されるように再正規化されます。成長率は`N`の連続したステップで平均化され、リャプノフ指数のスペクトルが得られます。

[^Lyapunov1992]: A. M. Lyapunov, *The General Problem of the Stability of Motion*, Taylor & Francis (1992)

[^Geist1990]: K. Geist *et al.*, Progr. Theor. Phys. **83**, pp 875 (1990)

[^Benettin1980]: G. Benettin *et al.*, Meccanica **15**, pp 9-20 & 21-30 (1980)

[^DatserisParlitz2022]: Datseris & Parlitz 2022, *Nonlinear Dynamics: A Concise Introduction Interlaced with Code*, [Springer Nature, Undergrad. Lect. Notes In Physics](https://doi.org/10.1007/978-3-030-91032-7)
