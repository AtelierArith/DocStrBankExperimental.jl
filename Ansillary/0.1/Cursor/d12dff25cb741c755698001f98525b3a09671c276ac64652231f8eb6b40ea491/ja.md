このモジュールはカーソルの制御に関するものです。

このモジュールの主な機能は、カーソルを移動させることと、カーソルを隠すことの2つです。

[`move!`](@ref) 関数を使用してカーソルを移動させます：

```julia
move!(Up(3))
```

利用可能なさまざまな移動方法があります。詳細については、[`Movement`](@ref) のサブタイプに関するドキュメントを参照してください。

[`save`](@ref) または [`checkpoint`](@ref) を使用して、一時的にカーソルを別の位置に移動させることも可能です：

```julia
move!(Coordinate(1, 1))
println("最初の行！")

save() do
	move!(Down(4))
	println("5行目！")

	checkpoint() do
		move!(Down(4))
		println("10行目！")

		checkpoint() do
			move!(Down(4))
			println("15行目！")
		end
	end
end

println("2行目！")

checkpoint() do
	move!(Down(4))
	println("6行目！")

	checkpoint() do
		move!(Down(4))
		println("11行目！");
	end
end
```

カーソルの位置は [`location`](@ref) を使用して見つけることもできますが、これは生モードでのみ機能することに注意してください：

```julia-repl
julia> Screen.raw(Cursor.location)
Ansillary.Inputs.Location(0x003c, 0x0001)
```

カーソルを隠すには、Julia の `do`-構文を使用します：

```julia-repl
julia> Cursor.hide() do
		   for c in "カーソルはありません..."
			   print(c)
			   sleep(0.1)
		   end
	   end
カーソルはありません...
```
