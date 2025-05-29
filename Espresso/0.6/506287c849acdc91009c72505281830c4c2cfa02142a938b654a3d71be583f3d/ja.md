式 `ex` をパターン `pat` に一致させ、一致したシンボルまたは rpatpressions の nullable 辞書を返します。例:

```
ex = :(u ^ v)
pat = :(_x ^ _n)
matchex(pat, ex)
# ==> Union{ Dict{Symbol,Any}(:_n=>:v,:_x=>:u), Void }
```

注意: 2つのシンボルは等しい場合、またはパターン内のシンボルがプレースホルダーである場合に一致します。プレースホルダーは、'*' で始まる任意のシンボルです。また、`phs` パラメータを介してプレースホルダー名のリスト（必ずしも '*' で始まる必要はありません）を渡すことも可能です:

```
ex = :(u ^ v)
pat = :(x ^ n)
matchex(pat, ex; phs=Set([:x, :n]))
# ==> Union{ Dict{Symbol,Any}(:n=>:v,:x=>:u), Void } 
```

複数の要素は `...` 式を使用して一致させることができます。例えば:

```
ex = :(A[i, j, k])
pat = :(x[I...])
matchex(pat, ex; phs=Set([:x, :I]))
# ==> Union{ Dict(:x=>:A, :I=>[:i,:j,:k]), Void }
```

オプションのパラメータ:

  * phs::Set{Symbol} = DEFAULT_PHS[1]     プレースホルダーシンボルのセット
  * allow_ex::Boolean = true     シンボルパターンを式に一致させることを許可します。例:

    ```
        matchex(:(_x + 1), :(a*b + 1); allow_ex=true)  # ==> 一致します
        matchex(:(_x + 1), :(a*b + 1); allow_ex=false)  # ==> 一致しません
    ```
  * exact::Boolean = false     同じ式を異なるキーに一致させることを許可します

    ```
        matchex(:(_x + _y), :(a + a); exact=false) # ==> 一致します
        matchex(:(_x = _y), :(a + a); exact=true)  # ==> 一致しません
    ```
