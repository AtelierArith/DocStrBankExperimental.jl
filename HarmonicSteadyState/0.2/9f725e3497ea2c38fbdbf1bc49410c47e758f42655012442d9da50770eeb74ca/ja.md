```
ウォームアップ
```

ウォームアップメソッドは、`index`でのパラメータを`perturbation_size`で摂動させて、トータルディグリーメソッドを使用したウォームアップシステムを準備します。ウォームアップシステムは、パラメータスイープ内の他のすべてのシステムを使用してホモトピーを実行するために使用されます。これは、パラメータスイープ内でのバイフurケーションが最小限のシステムに対して非常に効率的です。理論的には、ウォームアップメソッドはすべての解を見つけることを保証するはずですが、`start_parameters`が適切でない場合（実数直線に近すぎる場合）、いくつかの解を見逃す可能性があります。

詳細については、[HomotopyContinuation.jl](https://www.juliahomotopycontinuation.org/guides/many-systems/)を参照してください。

# フィールド

  * `warm_up_method::Union{HarmonicSteadyState.Polyhedral{T}, HarmonicSteadyState.TotalDegree{T}} where T`: ウォームアップシステムに使用されるメソッド。
  * `start_parameters::Vector`: 開始パラメータ。
  * `thread::Bool`: スレッドが有効かどうかを示すブール値。
  * `check_zero::Bool`: ゼロが根であるかどうかをチェック
  * `tracker_options::HomotopyContinuation.TrackerOptions`: トラッカーのオプション。
  * `endgame_options::HomotopyContinuation.EndgameOptions`: エンドゲームのオプション。
  * `compile::Union{Bool, Symbol}`: コンパイルオプション。
  * `seed::UInt32`: 乱数生成のためのシード。
