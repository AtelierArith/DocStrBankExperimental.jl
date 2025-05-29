```
NLLSsolver.computeresjac(varflags, mycost, vars...)
```

`mycost`によって生成された残差と、変数`vars`に示されたビットセットに対する導関数を計算します（最初のビットは最初の変数に対応し、その後も同様です）。戻り値はベクトルと行列でなければなりません。

# 例

ロゼンブロック問題の場合

```julia
struct Rosenbrock <: NLLSsolver.AbstractResidual
    a::Float64
    b::Float64
end
```

ユーザーは次の関数を定義する必要があります：

```julia
function NLLSsolver.computeresjac(varflags, res::Rosenbrock, x, y)
    res = SVector(res.a * (1 - x), res.b * (x ^ 2 - y))
    if varflags == 3
        jac = SMatrix{2, 2}(-res.a, 0.0, res.b * 2 * x, -res.b)
    else if varflags == 2
        jac = SVector(0.0, -res.b)
    else
        jac = SVector(-res.a, res.b * 2 * x)
    end
    return res, jac
end
```

!!! tip
    残差の長さがコンパイル時に知られている場合、静的ベクトルと静的行列を返してください。


!!! tip
    この関数をあなたの型に特化させる前に、デフォルトの自動微分関数を使用してみてください。


!!! note
    オプションのユーザー特化API関数です。

