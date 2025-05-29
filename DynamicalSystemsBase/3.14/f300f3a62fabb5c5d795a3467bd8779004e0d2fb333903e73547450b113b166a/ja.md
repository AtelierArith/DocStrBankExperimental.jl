```
ParallelDynamicalSystem <: DynamicalSystem
ParallelDynamicalSystem(ds::DynamicalSystem, states::Vector{<:AbstractArray})
```

与えられた力学系のいくつかの`states`を**まったく同じ時間で**並行して進化させる構造体です。これは、同じシステムの異なる軌道を進化させたいときに、パラメータと時間ベクトルを共有することを保証するのに便利です。

この構造体は、以下の調整を加えた[`DynamicalSystem`](@ref)インターフェースに従います：

  * 関数[`current_state`](@ref)は`current_state(pds, i::Int = 1)`として呼び出され、`i`番目の状態を返します。[`initial_state`](@ref)も同様です。
  * 同様に、[`set_state!`](@ref)は`i::Int = 1`という3番目の引数を取得して`i`番目の状態を設定します。
  * [`current_states`](@ref)と[`initial_states`](@ref)を使用して、すべての並行状態を取得できます。
  * [`reinit!`](@ref)は、`u`のために`states`のような状態のベクトルを受け取ります。

```
ParallelDynamicalSystem(ds::DynamicalSystem, states::Vector{<:Dict})
```

MTKモデルを参照する力学系の場合、`ds`の現在の状態を変更するために、辞書のベクトルとして状態を指定できます。これは[`set_state!`](@ref)のように行います。
