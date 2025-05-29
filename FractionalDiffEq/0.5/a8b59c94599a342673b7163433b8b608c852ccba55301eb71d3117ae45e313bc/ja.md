分数遅延微分方程 (FDDE) 問題を定義します。

## FDDE 問題の数学的仕様

FDDE 問題を定義するには、関数 $f$、履歴関数 $ϕ$、分数次数 $α$、遅延 $τ$、および初期条件 $u₀$ を指定する必要があります。これらは FDDE を定義します：

$$
D^\alpha_t y(t)=f(t,y(t),y(t-τ)),t ≥ 0
$$

$$
y(t)=ϕ(t), t ≤ 0
$$

`f` を指定する方法は二つあります：

  * `f(du,u,h,p,t)`：分数遅延微分方程式を記述する関数。
  * `f(u,h,p,t)`：`du` を返します。特に、変異が許可されていない場合（例えば、Zygote のような特定の自動微分パッケージを使用する場合）に適した、メモリ効率が良くない方法です。
  * `ϕ`：履歴関数
  * `α`：微分方程式の分数次数で、同次および非同次の両方がサポートされています。
  * `τ`：微分方程式の時間遅延。

## 問題の種類

### コンストラクタ

`FODEProblem` は、最初に `ODEFunction` を構築するか、単に FODE の右辺をコンストラクタに渡すことで構築できます。コンストラクタは次の通りです：

  * `FDDEProblem(f::ODEFunction,order,u0,ϕ,tspan,p=NullParameters();kwargs...)`
  * `FDDEProblem{isinplace,specialize}(f,order,u0,ϕ,tspan,p=NullParameters();kwargs...)`：指定された関数で FODE を定義します。`isinplace` は、関数がインプレースかどうかをオプションで設定します。これは自動的に決定されますが、推測されることはありません。`specialize` は、オプションで特化レベルを制御します。詳細については、[SciMLBase ドキュメントの特化レベルセクション](https://docs.sciml.ai/SciMLBase/stable/interfaces/Problems/#Specialization-Levels)を参照してください。デフォルトは `AutoSpecialize` です。

インプレースおよび特化制御の詳細については、ODEFunction ドキュメントを参照してください。

パラメータはオプションであり、指定されない場合は `NullParameters()` シングルトンが使用され、存在しないパラメータをインデックスしようとすると適切なエラーがスローされます。追加のキーワード引数はソルバーに渡されます。たとえば、問題に `callback` を設定すると、その `callback` はすべての解決呼び出しに追加されます。

ヤコビ行列や質量行列を指定するには、`ODEFunction` ドキュメントを参照してください。

### フィールド

  * `f`：FDDE 内の関数。
  * `ϕ`：FDDE 内の履歴関数。
  * `order`：FDDE の次数。
  * `τ`：FDDE の時間遅延。
  * `tspan`：問題の時間範囲。
  * `p`：パラメータ。
  * `kwargs`：解決に渡されるキーワード引数。

## 例題

```julia
function ϕ(p, t)
    if t == 0
        return 19.00001
    else
        return 19.0
    end
end
function f(y, ϕ, p, t)
    return 3.5 * y * (1 - ϕ / 19)
end
τ = [0.8]
order = 0.97
u0 = 19.00001
tspan = (0.0, 2.0)
dt = 0.5
prob = FDDEProblem(f, order, u0, ϕ, constant_lags = τ, tspan)
sol = solve(prob, DelayPIEX(), dt = dt)
```
