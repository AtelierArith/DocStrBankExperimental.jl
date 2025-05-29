```
squared_transfer(f, sdof::Oscillator)
```

周波数 `f` における SDOF システム `sdof` の伝達関数の二乗を計算します。

# 例

```julia-repl
	f = 2.0
	# 自然周波数 f_n=1.0 および減衰 ζ=0.05 の sdof を作成
	sdof = Oscillator( 1.0, 0.05 )
	Hf2 = squared_transfer( f, sdof )
```

参照: [`transfer`](@ref)
