```julia
writelines(
    x::AbstractVector{<:AbstractString},
    f::AbstractString;
    mode,
    eof
)

```

# 引数

  * `mode`:

モード 説明 キーワード                    –––– ––––––––––– –––––––––––––––––––––––––   r    読み取り        なし                        w    書き込み       write = true                r+   読み取り、書き込み read = true, write = true   w+   読み取り、書き込み read = true, write = true

# @seealso readlines

! `x` はstringである必要があります。そうでないとファイルエラーが発生します。
