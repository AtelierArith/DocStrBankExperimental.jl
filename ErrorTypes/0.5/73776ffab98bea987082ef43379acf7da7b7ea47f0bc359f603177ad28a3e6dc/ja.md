```
expect(x::Result, s::AbstractString)
```

`x`が関連するエラータイプの場合、メッセージ`s`でエラーを発生させます。そうでなければ、含まれている結果タイプを返します。

参照: [`expect_error`](@ref), [`unwrap`](@ref)

# 例

```jldoctest
julia> expect(some('x'), "cannot be none") === 'x'
true

julia> expect(Result{Int, String}(Ok(19)), "Expected an integer")
19
```
