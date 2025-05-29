```
FastShortcutNonlinearPolyalg(
    ::Type{T} = Float64;
    concrete_jac = nothing,
    linsolve = nothing,
    must_use_jacobian::Val = Val(false),
    prefer_simplenonlinearsolve::Val = Val(false),
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing,
    u0_len::Union{Int, Nothing} = nothing
) where {T}
```

速度と堅牢性のバランスに焦点を当てたポリアルゴリズムです。最初にパフォーマンスを向上させるために堅牢性の低い手法を試し、次に高速な手法が失敗した場合により堅牢な技術を試みます。

### 引数

  * `T`: 初期推定のエルタイプです。これは、いくつかのアルゴリズムが問題のタイプと互換性があるかどうかを確認するためにのみ使用されます。デフォルトは `Float64` です。

### キーワード引数

  * `u0_len`: 初期推定の長さです。これが `nothing` の場合、初期推定の長さはチェックされません。これが整数で `25` 未満の場合、ヤコビアンに基づく手法を使用します。
