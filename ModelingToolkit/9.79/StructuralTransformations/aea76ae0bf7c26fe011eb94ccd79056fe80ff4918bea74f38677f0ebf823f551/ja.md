```julia
full_equations(
    sys::ModelingToolkit.AbstractSystem;
    simplify
) -> Any

```

`equations(sys)`と同様ですが、テアリングプロセスによって行われた置換を含みます。これらの方程式は生成された数値コードと一致します。

[`equations`](@ref)および[`ModelingToolkit.get_eqs`](@ref)も参照してください。
