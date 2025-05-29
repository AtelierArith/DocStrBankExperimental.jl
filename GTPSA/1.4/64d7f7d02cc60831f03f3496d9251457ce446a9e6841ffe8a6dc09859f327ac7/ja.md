```
@FastGTPSA(expr_or_block)
```

数式の評価を高速化するためのマクロで、TPSを含む数式の評価中に生成される一時変数はスレッドセーフなバッファから取得され、結果のヒープ割り当ての数を2（単一のTPS用）に減らします。@FastGTPSAは他のすべての型に対して完全に透過的であるため、型に依存しないコードを維持しながら式の前に追加することができます。

```julia-repl
julia> using GTPSA, BenchmarkTools

julia> d = Descriptor(3,7); Δx = @vars(d);

julia> t = @btime $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
  3.458 μs (20 allocations: 11.88 KiB)

julia> t = @btime @FastGTPSA $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
  3.172 μs (2 allocations: 1.94 KiB)
```

`@FastGTPSA`はコードブロックの前にも追加でき、その場合はブロック内のすべての`=`記号の後に適用されます：

```julia-repl
julia> @btime @FastGTPSA begin
       t1 = $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
       t2 = $Δx[1]^3*sin($Δx[2])/log(2+$Δx[3])-exp($Δx[1]*$Δx[2])*im;
       a = t1+t2
       L = 5+3*exp(7)
       end
  6.317 μs (6 allocations: 5.81 KiB)
```

ブロードキャスティングも`@FastGTPSA`と互換性があります（`TPS`ごとに2つの割り当てと`Array`ごとに1つの割り当てに注意）：

```julia-repl
julia> using GTPSA, BenchmarkTools

julia> d = Descriptor(3, 7); Δx = @vars(d); y = rand(3);

julia> @btime @FastGTPSA begin
        out = @. $Δx^3*sin($y)/log(2+$x)-exp($x*$y)*im;
       end;
  7.573 μs (7 allocations: 5.89 KiB)
```
