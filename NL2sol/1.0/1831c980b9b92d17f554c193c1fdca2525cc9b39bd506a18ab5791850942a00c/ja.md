```
nl2solは非線形最小二乗問題を解決します。つまり、xがサイズpのベクトルであるとき、sum(i=1:n){r_i(x)^2}を最小化するxを見つけます。
関連情報を含むOptim.MultivariateOptimizationResults型の構造体を返します（詳細についてはOptimのドキュメントを参照してください）。

残差とヤコビ行列の関数は、これらの値のために事前に割り当てられた引数を受け取ることが期待されています。これらの配列は、Fortranのサブルーチンnl2solに渡す前に、Juliaの関数nl2sol内で実際に割り当てられます。

注意: NL2sol.jlはFORTRANコードとインターフェースするためにポインタートリックを行うため、コードを変更したい場合は注意してください。

使用例

using NL2sol

function rosenbrock_res(x, r)
    r[1] = 10. * (x[2] - x[1]^2 )
    r[2] = 1. - x[1]
    return r
end

function rosenbrock_jac(x, jac)
    jac[1, 1] = -20.0 * x[1]
    jac[1, 2] =  10.0
    jac[2, 1] =  -1.0
    jac[2, 2] =   0.0
   return jac
end

function main()
    println("NL2SOL on Rosenbrock")
    result = nl2sol(rosenbrock_res, rosenbrock_jac, [-1.2, 1.0], 2; quiet=true)
    println(result)
end

main()
```
