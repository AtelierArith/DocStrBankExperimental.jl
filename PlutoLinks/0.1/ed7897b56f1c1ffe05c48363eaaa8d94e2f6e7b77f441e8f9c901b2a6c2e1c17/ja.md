`Task`を現在のセルでラップします。セルの状態がリセットされると、基になる`Task`に`InterruptException`を送信します。

```julia
@use_task([]) do
	while true
		sleep(2.)
		@info "this is updating"
	end
end
```

値のバックグラウンド更新のために`@use_state`と組み合わせることができます。

`deps=nothing`をデフォルトにするのが最良か、`deps=[]`にするか、あるいは明示的にdepsを要求して人々が自分のやっていることを理解するように強制するのが良いか、まだ考えています。
