コードブロックをデバウンスを使用して実行します。つまり、変数リストが `timeout` を通じて安定したときのみ実行します。

```julia
@use_debounce([var], 1) do
	sleep(2.)
	@info "stable variable $var"
end
```
