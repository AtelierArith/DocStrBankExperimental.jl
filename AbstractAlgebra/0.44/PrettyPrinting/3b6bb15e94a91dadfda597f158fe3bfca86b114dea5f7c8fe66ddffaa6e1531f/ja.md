```
with_unicode(f::Function, allowed::Bool=true)
```

`f`の実行中に、きれいな印刷でUnicode文字が許可されるかどうかを一時的に設定します。これは、ユーザーの好みに応じてドクトテストを独立して実行するのに便利です。

`with_unicode`は次のように呼び出されることが期待されています：

```julia
with_unicode([allowed]) do
   # Unicodeが許可/不許可で実行されるべきコード
end
```

[`allow_unicode`](@ref)および[`is_unicode_allowed`](@ref)も参照してください。
