```
run_spineopt(f, url_in, url_out; <keyword arguments>)
```

`run_spineopt(url_in, url_out; kwargs...)` と同じですが、SpineOpt モデルが作成された直後（構築と解決の前）に引数として関数 `f` を呼び出します。

これは do ブロック構文を使用して呼び出すことを意図しています。

```julia
run_spineopt(url_in, url_out) do m
    # m の作成後に何かを行う
end  # このブロックを抜けた後に構築と解決が始まります
```
