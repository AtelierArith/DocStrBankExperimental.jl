```
@FastGTPSA!(expr_or_block)
```

数式の評価を高速化するマクロで、事前に割り当てられた `TPS` への代入を含む可能性があります。式の評価中に生成される一時変数は、スレッドセーフなバッファから取得されます。このマクロを使用すると、`TPS` を含む式の評価中のヒープ割り当ての数は 0 になり、非 `TPS` 型に対しても完全に透過的です。

このマクロは、`=`, `+=`, `-=`, `*=`, `/=`, および `^=` を使用した代入をサポートしています。

**重要:** シンボルは、型が `TPS` であるかどうかに関係なく、マクロを呼び出す前に定義されている必要があります：

```julia-repl
julia> using GTPSA, BenchmarkTools

julia> d = Descriptor(3,7); Δx = @vars(d); 

julia> t = ComplexTPS64(); # 事前に割り当て

julia> @btime @FastGTPSA! $t = $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
  2.972 μs (0 allocations: 0 bytes)

julia> @btime @FastGTPSA! $t ^= $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
  6.550 μs (0 allocations: 0 bytes)

julia> y = rand(3); z = 2; # 非 TPS 型に対して透過的 

julia>  @btime @FastGTPSA! $z = $y[1]^3*sin($y[2])/log(2+$y[3])-exp($y[1]*$y[2])*im;
  11.344 ns (0 allocations: 0 bytes)
```

`@FastGTPSA` と同様に、`@FastGTPSA!` はコードのブロックの前に付けることができ、その場合、代入を含むブロック内の各行の前に適用されます：

```julia-repl
julia> t1 = zero(ComplexTPS64); t2 = zero(ComplexTPS64); z = 0; 

julia> @btime @FastGTPSA! begin
       $t1 = $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
       $t2 -= $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
       $z += 7
       end
  5.965 μs (0 allocations: 0 bytes)
```

ブロードキャスティングも `@FastGTPSA!` と互換性があります：

```julia-repl
julia> using GTPSA, BenchmarkTools

julia> d = Descriptor(3, 7); Δx = @vars(d); y = rand(3);

julia> out = zeros(ComplexTPS64, 3) # 事前に割り当て

julia> @btime @FastGTPSA! begin
        @. $out = $Δx^3*sin($y)/log(2+$Δx)-exp($Δx*$y)*im;
       end;
  7.312 μs (0 allocations: 0 bytes)
```
