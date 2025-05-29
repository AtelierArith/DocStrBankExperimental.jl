```
UnspecifiedParallel{C,S} <: AbstractParallel{C,S}
```

明示的に治療群間の関係が指定されていない平行トレンド仮定（PTA）。詳細は[`unspecifiedpr`](@ref)を参照してください。

この平行タイプでは、PTAに従うための操作が抑制されます。これは、ユーザーが提供した回帰変数やサンプル制限をPTA特有の変更なしに受け入れる必要がある場合に便利です。

# フィールド

  * `c::C`: [`ParallelCondition`](@ref)のインスタンス。
  * `s::S`: [`ParallelStrength`](@ref)のインスタンス。
