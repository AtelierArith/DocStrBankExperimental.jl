```
JLMatch <: JLExpr
```

`JLMatch`は、[`MLStyle`](https://github.com/thautwarm/MLStyle.jl)によって定義されたJuliaパターンマッチ式を説明します。これは、各コードブロックを対応するパターン式に単純に割り当てることで、そのような式を構築することを可能にします。

!!! tip
    `JLMatch`は、MLStyleのパターンマッチ機能に依存しているため、ExproniconLiteでは利用できません。


# 例

対応するパターンとその結果を`map`フィールドに割り当てることで、`MLStyle`パターンマッチ式を簡単に構築できます。

```julia
julia> jl = JLMatch(:x)
#= line 0 =#
nothing

julia> jl = JLMatch(:x)
#= line 0 =#
nothing

julia> jl.map[1] = true
true

julia> jl.map[2] = :(sin(x))
:(sin(x))

julia> jl
#= line 0 =#
@match x begin
    1 => true
    2 => sin(x)
    _ =>     nothing
end
```

対応するJulia `Expr`オブジェクトを生成するには、[`codegen_ast`](@ref)を呼び出すことができます。

```julia
julia> codegen_ast(jl)
:(let
      true
      var"##return#263" = nothing
      var"##265" = x
      if var"##265" isa Int64
          #= line 0 =#
          if var"##265" === 1
              var"##return#263" = let
                      true
                  end
              #= unused:1 =# @goto var"####final#264#266"
          end
          #= line 0 =#
          if var"##265" === 2
              var"##return#263" = let
                      sin(x)
                  end
              #= unused:1 =# @goto var"####final#264#266"
          end
      end
      #= line 0 =#
      begin
          var"##return#263" = let
                  nothing
              end
          #= unused:1 =# @goto var"####final#264#266"
      end
      (error)("matching non-exhaustive, at #= line 0 =#")
      #= unused:1 =# @label var"####final#264#266"
      var"##return#263"
  end)
```
