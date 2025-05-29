```julia
struct BifFunction{Tf, TFinp, Tdf, Tdfad, Tj, Tjad, TJinp, Td2f, Td2fc, Td3f, Td3fc, Tδ, Tjet} <: BifurcationKit.AbstractBifurcationFunction
```

ベクトル場とその導関数を保持する構造体です。直接呼び出されることは稀であるべきです。また、本質的には `SciMLBase.ODEFunction` に非常に近いです。

## フィールド

  * `F::Any`: ベクトル場。タイプの関数で、アウトオブプレース `result = f(x, p)` またはインプレース `f(result, x, p)`。型の安定性のために、`x` と `result` の型は一致するべきです。
  * `F!::Any`: Fと同じですが、インプレースでシグネチャは F!(result, x, p) です。
  * `dF::Any`: `x` に関する `F` の微分、シグネチャ `dF(x,p,dx)`。
  * `dFad::Any`: `x` に関する `F` の微分の随伴、シグネチャ `dFad(x,p,dx)`。
  * `J::Any`: `(x, p)` における `F` のヤコビ行列。3つの形を取ることができます。         1. `J` が関数であり、`J(x, p)` が `::AbstractMatrix` を返す場合。この場合、`contparams::ContinuationPar` のデフォルト引数により `continuation` が機能します。         2. または `J` が関数であり、`J(x, p)` が1つの引数 `dx` を取り、`dx` と同じ型の `dr` を返す関数を返す場合。この場合、`dr = J * dx` となります。この場合、`contparams::ContinuationPar` のデフォルトパラメータは機能せず、例えば `GMRESIterativeSolvers` のようなマトリックスフリーの線形ソルバーを使用する必要があります。         3. または `J` が関数であり、`J(x, p)` が任意の型を取る変数 `j` を返す場合。この場合、`ls(j, rhs)` のように呼び出され、ヤコビ行列線形系の解を返す合成型の線形ソルバー `ls` を実装する必要があります。例えば `examples/SH2d-fronts-cuda.jl` を参照してください。この線形ソルバーは `NewtonPar(linsolver = ls)` に渡され、さらに `ContinuationPar` に渡されます。同様に、合成型の固有値ソルバー `eig` を `AbstractEigenSolver` のサブタイプとして実装する必要があります。
  * `Jᵗ::Any`: ヤコビ行列の随伴で、効率的に実装されるべきです。マトリックスフリーの手法では、`transpose` はすぐには利用できず、ユーザーは専用のメソッドを提供する必要があります。スパースベースのヤコビ行列の場合、`Jᵗ` は内部でより効率的に計算されるため渡すべきではありません。つまり、`Jᵗ = (x, p) -> transpose(dF(x, p))` のように渡すと、ヤコビ行列を再計算することになります。
  * `J!::Any`: インプレースヤコビ行列
  * `d2F::Any`: `x` に関する `F` の第二微分、シグネチャ `d2F(x,p,dx1,dx2)`。
  * `d3F::Any`: `x` に関する `F` の第三微分、シグネチャ `d3F(x,p,dx1,dx2,dx3)`。
  * `d2Fc::Any`: [内部] 複素ベクトル dxi を受け入れる `x` に関する `F` の第二微分。
  * `d3Fc::Any`: [内部] 複素ベクトル dxi を受け入れる `x` に関する `F` の第三微分。
  * `isSymmetric::Bool`: ヤコビ行列が自己随伴であるかどうか。
  * `δ::Any`: 導関数を計算するために内部で使用されます（有限差分を使用）、例えば正規形計算やコディメンション2の継続のために。
  * `inplace::Bool`: 関数がインプレースかどうかをオプションで設定します。現在の状態がバイセクションモードにあるかどうかを確認するには `in_bisection(state)` を使用できます。
  * `jet::Any`: ベクトル場のジェット

## メソッド

  * `residual(pb::BifFunction, x, p)` は `pb.F(x,p)` を呼び出します。
  * `jacobian(pb::BifFunction, x, p)` は `pb.J(x, p)` を呼び出します。
  * `dF(pb::BifFunction, x, p, dx)` は `pb.dF(x,p,dx)` を呼び出します。
  * `R21(pb::BifFunction, x, p, dx1, dx2, dp1)` は `pb.jet.R21(x, p, dx1, dx2, dp1)` を呼び出します。他のジェット関数についても同様です。
  * など

```
