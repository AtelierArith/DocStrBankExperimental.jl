```
nilang_ir(ex; reversed::Bool=false)
```

Get the NiLang reversible IR from the function expression `ex`, return the reversed function if `reversed` is `true`.

This IR is not directly executable on Julia, please use `macroexpand(Main, :(@i function .... end))` to get the julia expression of a reversible function.

```jldoctest; setup=:(using NiLangCore)
julia> ex = :(@inline function f(x!::T, y) where T
                @routine begin
                    anc ← zero(T)
                    anc += identity(x!)
                end
                x! += y * anc
                ~@routine
           end);

julia> NiLangCore.nilang_ir(Main, ex) |> NiLangCore.rmlines
:(@inline function f(x!::T, y) where T
          begin
              anc ← zero(T)
              anc += identity(x!)
          end
          x! += y * anc
          begin
              anc -= identity(x!)
              anc → zero(T)
          end
      end)

julia> NiLangCore.nilang_ir(Main, ex; reversed=true) |> NiLangCore.rmlines
:(@inline function (~f)(x!::T, y) where T
          begin
              anc ← zero(T)
              anc += identity(x!)
          end
          x! -= y * anc
          begin
              anc -= identity(x!)
              anc → zero(T)
          end
      end)
```
