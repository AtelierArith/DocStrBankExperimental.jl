```
FastShortcutNLLSPolyalg(
    ::Type{T} = Float64;
    concrete_jac = nothing,
    linsolve = nothing,
    autodiff = nothing, vjp_autodiff = nothing, jvp_autodiff = nothing
)
```

速度と堅牢性のバランスに焦点を当てたポリアルゴリズムです。最初は、より高いパフォーマンスのために堅牢性の低い手法を試し、次に、より速い手法が失敗した場合に堅牢な技術を試みます。

### 引数

  * `T`: 初期推定値のエルタイプです。これは、いくつかのアルゴリズムが問題のタイプと互換性があるかどうかを確認するためにのみ使用されます。デフォルトは `Float64` です。
