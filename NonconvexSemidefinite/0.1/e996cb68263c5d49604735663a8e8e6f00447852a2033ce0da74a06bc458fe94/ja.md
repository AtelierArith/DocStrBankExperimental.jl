```
SDPBarrierAlg(sub_alg)
```

非線形関数に対する半正定値制約をバリアアプローチを使用して処理するメタアルゴリズムです。バリア項の係数は指数関数的に減衰し、サブ問題は `sub_alg` を使用して解決されます。 `sub_alg` は `Nonconvex.jl` からの他の互換性のあるソルバーであれば何でもかまいません。ソルバーは、半正定値制約を取り除いた後にサブ問題を解決できる必要があります。ソルバーへのオプションは [`SDPBarrierOptions`](@ref) 構造体に渡され、`optimize` 関数へのオプションとして渡されるべきです。すべての異なるオプションを確認するには `? SDPBarrierOptions` を呼び出してください。
