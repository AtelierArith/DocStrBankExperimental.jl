分数常微分方程 (FODE) 問題を定義します。

## FODE 問題の数学的仕様

FODE 問題を定義するには、関数 $f$ と初期条件 $u_0$ を指定するだけで、FODE を定義できます：

$$
\frac{du^\alpha}{d^{\alpha}t} = f(u,p,t)
$$

`f` を指定する方法は二つあります：

  * `f(du,u,p,t)`：インプレース。メモリ効率が良く、アロケーションを避けることができます。変異が許可されていない限り、ほとんどのケースで最良の選択肢です。
  * `f(u,p,t)`：`du` を返します。メモリ効率が悪い方法ですが、特に変異が許可されていない場合（例えば、Zygote のような特定の自動微分パッケージを使用する場合）に適しています。
  * `order`：微分方程式の分数次数で、同次および非同次の両方がサポートされています。-`u₀` は、`u` の望ましい幾何学に一致する AbstractArray（または数）である必要があります。`u₀` に対して数やベクトルに制限されることはなく、任意の行列や高次元テンソルを提供することも許可されています。

## 問題の種類

### コンストラクタ

`FODEProblem` は、最初に `ODEFunction` を構築するか、単に FODE の右辺をコンストラクタに渡すことで構築できます。コンストラクタは次の通りです：

  * `FODEProblem(f::ODEFunction,u0,tspan,p=NullParameters();kwargs...)`
  * `FODEProblem{isinplace,specialize}(f,u0,tspan,p=NullParameters();kwargs...)`：指定された関数で FODE を定義します。`isinplace` は、関数がインプレースかどうかをオプションで設定します。これは自動的に決定されますが、推測されることはありません。`specialize` は、オプションで特化レベルを制御します。詳細については、[SciMLBase ドキュメントの特化レベルセクション](https://docs.sciml.ai/SciMLBase/stable/interfaces/Problems/#Specialization-Levels)を参照してください。デフォルトは `AutoSpecialize` です。

インプレースおよび特化制御の詳細については、ODEFunction ドキュメントを参照してください。

パラメータはオプションであり、指定されない場合は `NullParameters()` シングルトンが使用され、存在しないパラメータにインデックスを付けようとすると適切なエラーがスローされます。追加のキーワード引数はソルバーに渡されます。たとえば、問題に `callback` を設定すると、その `callback` はすべての解決呼び出しに追加されます。

ヤコビ行列や質量行列を指定するには、`ODEFunction` ドキュメントを参照してください。

### フィールド

  * `f`：ODE の関数。
  * `order`：FODE の次数。
  * `u0`：初期条件。
  * `tspan`：問題の時間範囲。
  * `p`：パラメータ。
  * `kwargs`：解決に渡されるキーワード引数。

## 例題

```julia
using SciMLBase
function lorenz!(du, u, p, t)
    du[1] = 10.0(u[2] - u[1])
    du[2] = u[1] * (28.0 - u[3]) - u[2]
    du[3] = u[1] * u[2] - (8 / 3) * u[3]
end
order = [0.96; 0.96; 0.96]
u0 = [1.0; 0.0; 0.0]
tspan = (0.0, 100.0)
prob = FODEProblem(lorenz!, u0, tspan)

# 正常に動作したかテスト
using FractionalDiffEq
sol = solve(prob, PIEX())
using Plots;
plot(sol, vars = (1, 2, 3));
```
