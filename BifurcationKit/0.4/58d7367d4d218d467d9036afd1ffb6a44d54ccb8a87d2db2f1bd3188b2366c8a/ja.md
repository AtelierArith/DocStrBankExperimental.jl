```julia
struct PeriodicOrbitTrapProblem{Tprob, vectype, Tls<:BifurcationKit.AbstractLinearSolver, T, Tmass} <: BifurcationKit.AbstractPOFDProblem
```

この複合型は、周期軌道を特定するために台形法（時間における2次）に基づく有限差分を実装しています。詳細（数学、表記、線形システム）については[こちら](https://bifurcationkit.github.io/BifurcationKitDocs.jl/dev/periodicOrbitTrapeze/)を参照してください。

スキームは次のとおりです。まず、$[0,1]$の分割を$0<s_0<\cdots<s_m=1$として考え、`T = x[end]`を見つけることを考えます。

$$
M_a\cdot\left(x_{i} - x_{i-1}\right) - \frac{T\cdot h_i}{2} \left(F(x_{i}) + F(x_{i-1})\right) = 0,\ i=1,\cdots,m-1
$$

ここで$u_{0} := u_{m-1}$および周期条件$u_{m} - u_{1} = 0$が成り立ちます。

$$
h_1 = s_i-s_{i-1}
$$

です。$M_a$は質量行列です。最後に、周期軌道の位相はセクションを使用して制約されます（ただし、独自のものを使用することもできます）。

$$
\sum_i\langle x_{i} - x_{\pi,i}, \phi_{i}\rangle=0.
$$

## フィールド

  * `prob_vf::Any`: 分岐問題 デフォルト: なし
  * `ϕ::Any`: 位相制約方程式のためのセクションを設定するために使用される、サイズN*M デフォルト: なし
  * `xπ::Any`: 位相制約方程式のためのセクションで使用される、サイズN*M デフォルト: なし
  * `M::Int64`: 時間スライスの数 デフォルト: 0
  * `mesh::BifurcationKit.TimeMesh`: メッシュ、`TimeMesh`を参照 デフォルト: TimeMesh(M)
  * `N::Int64`: `AbstractVector`の場合の問題の次元 デフォルト: 0
  * `linsolver::BifurcationKit.AbstractLinearSolver`: 各時間スライスのための線形ソルバー、すなわち`J⋅sol = rhs`を解くためのもの。これは、完全なマトリックスフリー設定でFloquet倍数を計算するためにのみ必要です。 デフォルト: DefaultLS()
  * `ongpu::Bool`: 計算がGPU上で行われるかどうか（実験的） デフォルト: false
  * `isautonomous::Bool`: デフォルト: true
  * `massmatrix::Any`: 質量行列。例えば、スパース行列を渡すことができます。 デフォルト: 単位行列。 デフォルト: なし
  * `update_section_every_step::UInt64`: 継続中に`update_section_every_step`ステップごとにセクションを更新 デフォルト: 1
  * `jacobian::Symbol`: ニュートン反復で使用されるヤコビ行列のタイプを記述するシンボル（下記参照）。 デフォルト: :Dense

## コンストラクタ

この構造体は`PeriodicOrbitTrapProblem(;kwargs...)`を呼び出すことで作成できます。たとえば、ベクトルフィールドなしでこのような問題を宣言することができます。

```
PeriodicOrbitTrapProblem(M = 100)
```

# 軌道の推測

以下に示すように、軌道の推測`orbitguess`に対して`pb(orbitguess, p)`を呼び出すことで、機能の残差（および他のもの）を評価できます。`orbitguess`はサイズM * N + 1のベクトルでなければならず、ここでNは状態空間の未知数の数であり、`orbitguess[M*N+1]`はリミットサイクルの周期$T$の推定値です。より正確には、上記の表記を使用すると、`orbitguess`は$orbitguess = [x_{1},x_{2},\cdots,x_{M}, T]$でなければなりません。

この推測は、`generate_solution`または`generate_ci_problem`を使用して関数解から生成できます。

# 機能

機能は、ここで`G`と呼ばれ、この問題をエンコードします。以下のメソッドが利用可能です。

  * `pb(orbitguess, p)`は`orbitguess`上の機能Gを評価します。
  * `pb(orbitguess, p, du)`は`du`上の`orbitguess`でのヤコビ行列`dG(orbitguess).du`機能を評価します。
  * `pb(Val(:JacFullSparse), orbitguess, p)`は制約なしで`orbitguess`でのヤコビ行列`dG(orbitguess)`のスパース行列を返します。これはドキュメントでは`A_γ`と呼ばれています。
  * `pb(Val(:JacFullSparseInplace), J, orbitguess, p)`。これは`pb(Val(:JacFullSparse), orbitguess, p)`と同じですが、`J`をインプレースで上書きします。ここで、スパースパターンはパラメータの値や`orbitguess`に関係なく常に同じでなければなりません。この場合、これは`pb(Val(:JacFullSparse), orbitguess, p)`よりも大幅に高速です。
  * `pb(Val(:JacCyclicSparse), orbitguess, p)`は`orbitguess`でのヤコビ行列`dG(orbitguess)`のスパース循環行列Jc（ドキュメント参照）を返します。
  * `pb(Val(:BlockDiagSparse), orbitguess, p)`は`orbitguess`でのヤコビ行列`dG(orbitguess)`のスパース行列の対角成分を返します。これにより、ヤコビ前処理器を設計できます。`blockdiag`を使用してください。

# ヤコビ行列

ヤコビ行列（および線形アルゴリズム）の選択を指定します。`jacobian`は`[:FullLU, :FullSparseInplace, :Dense, :DenseAD, :BorderedLU, :BorderedSparseInplace, :FullMatrixFree, :BorderedMatrixFree, :FullMatrixFreeAD]`のいずれかでなければなりません。これは、機能Gのヤコビ行列`dG`を反転する方法を選択するために使用されます。

  * `jacobian = :FullLU`の場合、`dG`のスパース行列表現に基づくデフォルトの線形ソルバーを使用します。この行列は、各ニュートン反復で組み立てられます。これはデフォルトのアルゴリズムです。
  * `jacobian = :FullSparseInplace`の場合、これは`:FullLU`と同じですが、スパース行列`dG`がインプレースで更新されます。この方法は、はるかに少ないメモリを割り当てます。場合によっては、`:FullLU`を使用するよりも大幅に高速です。この方法は、ヤコビ行列のスパースパターンが常に同じである場合にのみ使用できます。
  * `jacobian = :Dense`の場合、上記と同じですが、行列`dG`は密です。また、インプレースで更新されます。このオプションは、小さな次元のODEを研究するのに便利です。
  * `jacobian = :DenseAD`の場合、ForwardDiffを使用してヤコビ行列を評価します。
  * `jacobian = :BorderedLU`の場合、線形ソルバーの境界形状を利用し、LU分解を使用して`dG`を反転します。
  * `jacobian = :BorderedSparseInplace`の場合、これは`:BorderedLU`と同じですが、循環行列`dG`がインプレースで更新されます。この方法は、はるかに少ないメモリを割り当てます。場合によっては、`:BorderedLU`を使用するよりも大幅に高速です。この方法は、ヤコビ行列のスパースパターンが常に同じである場合にのみ使用できます。
  * `jacobian = :FullMatrixFree`の場合、`dG`に対してマトリックスフリーの線形ソルバーが使用されます。ここでは、`dG`の循環形状がGMRESの収束特性に悪影響を及ぼすため、前処理器が必要になる可能性が非常に高いことに注意してください。
  * `jacobian = :BorderedMatrixFree`の場合、マトリックスフリーの線形ソルバーが使用されますが、`Jc`のみに対して（ドキュメント参照）使用されます。これは、`options.linsolver`が`Jc`を反転するために使用されることを意味します。これらの2つのマトリックスフリーオプションは、特定の前処理器を使用するために、ヤコビ行列`dG`の異なる部分を公開します。たとえば、`Jc`に対するILU前処理器は、`dG`の制約を削除し、収束を悪化させる可能性があります。もちろん、これらの最後の2つの方法では、前処理器が必要になる可能性が高いです。
  * `jacobian = :FullMatrixFreeAD`の場合、微分の評価マップは自動微分を使用して導出されます。したがって、前の2つのケースとは異なり、ユーザーはマトリックスフリーの微分を渡す必要はありません。

!!! note "GPU呼び出し"
    これらのメソッドがGPU上で機能するためには、たとえば`CuArrays`を`allowscalar(false)`モードで使用する場合、関数`_extract_period_fdtrap`がスカラー操作であるため、適切に定義されないという問題に直面します。機能がGPU上で効率的に評価されるためには、オプション`ongpu = true`を渡す必要があることに注意してください。

