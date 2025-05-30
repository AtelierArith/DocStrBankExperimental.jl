```julia
struct ExtendedJumpArray{T3<:Number, T1, T<:AbstractArray{T3<:Number, T1}, T2} <: AbstractArray{T3<:Number, 1}
```

`VariableRateJump`がシステムに存在する場合に、積分器内で使用される拡張状態定義。詳細な例と使用情報については、以下を参照してください。

  * [Tutorial](https://docs.sciml.ai/JumpProcesses/stable/tutorials/discrete_stochastic_example/)

### フィールド

  * `u`: 現在の状態。
  * `jump_u`: `VariableRateJump`の現在のレート（すなわち、ハザード、強度、または傾向）値。

## 例

```julia
using JumpProcesses, OrdinaryDiffEq
f(du,u,p,t) = du .= 0
rate(u,p,t) = (1+t)*u[1]*u[2]

# ジャンプが発生したときに2つの変数のそれぞれを1ずつ減少させたいとします
function affect!(integrator)
   # メソッド1、直接インデックス指定は通常通りに機能します
   integrator.u[1] -= 1
   integrator.u[2] -= 1

   # メソッド2、ブロードキャストまたは配列操作を使用したい場合は、
   # integrator.u.uにアクセスする必要があります。これは実際の状態オブジェクトです。
   # したがって、上記と同等に次のように言うこともできます：
   # integrator.u.u .-= 1
end

u0 = [10.0, 10.0]
vrj = VariableRateJump(rate, affect!)
oprob = ODEProblem(f, u0, (0.0,2.0))
jprob = JumpProblem(oprob, Direct(), vrj)
sol = solve(jprob,Tsit5())
```

## 注意事項

  * `ueja isa ExtendedJumpArray` で `ueja.u` のサイズが `N` で、`ueja.jump_u` のサイズが `num_variableratejumps` の場合、次のようになります。

    ```julia
    # 1 <= i <= N の場合
    ueja[i] == ueja.u[i]

    # N < i <= (N+num_variableratejumps) の場合
    ueja[i] == ueja.jump_u[i]
    ```
  * `VariableRateJump`を持つシステムでは、すべてのコールバック、`ConstantRateJump`、および`VariableRateJump`の`affect!`関数は、`integrator.u`が`ExtendedJumpArray`である積分器を受け取ります。
  * そのため、ベクトル操作を介して状態を変更したい`affect!`関数は、エイリアスされた状態オブジェクトを取得するために`ueja.u.u`を使用する必要があります。
