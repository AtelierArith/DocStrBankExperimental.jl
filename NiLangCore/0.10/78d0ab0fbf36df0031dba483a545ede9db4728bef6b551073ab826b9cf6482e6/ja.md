```
nilang_ir(ex; reversed::Bool=false)
```

関数式 `ex` から NiLang 可逆 IR を取得し、`reversed` が `true` の場合は逆関数を返します。

この IR は直接 Julia で実行できません。可逆関数の Julia 式を取得するには、`macroexpand(Main, :(@i function .... end))` を使用してください。

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
