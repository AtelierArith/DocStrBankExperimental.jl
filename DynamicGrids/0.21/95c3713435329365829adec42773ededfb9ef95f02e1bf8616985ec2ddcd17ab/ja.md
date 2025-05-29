```
sim!(output, rules::Rule...; kw...)
sim!(output, rules::Tuple{<:Rule,Vararg}; kw...)
sim!(output, [ruleset::Ruleset=ruleset(output)]; kw...)
```

`output`の`tspan`に対してシミュレーションルールを実行し、各タイムステップの宛先配列を`output`に書き込みます。

# 引数

  * `output`: グリッドを保存するか、画面に表示するための[`Output`](@ref)。
  * `ruleset`: 1つ以上の[`Rule`](@ref)を含む[`Ruleset`](@ref)。出力に`Ruleset`が添付されている場合、それが使用されます。

# キーワード

これらはデフォルトで`output`引数から取得されます：

  * `init`: オプションの配列または配列のNamedTuple。
  * `mask`: 初期配列のサイズに一致する`Bool`配列。`false`のセルは実行されません。
  * `aux`: ルールによって使用される補助データのNamedTuple。
  * `tspan`: シミュレーションが実行される時間範囲の開始と終了を保持するタプル。
  * `fps`: 表示するフレーム毎秒。渡されない場合は出力から取得されます。

これらはデフォルトで`ruleset`引数から取得されます：

  * `proc`: [`SingleCPU`](@ref)、[`ThreadedCPU`](@ref)または[`CuGPU`](@ref)のように、シミュレーションを実行するハードウェアを指定する[`Processor`](@ref)。
  * `opt`: [`SparseOpt`](@ref)や[`NoOpt`](@ref)のような最適化を指定する[`PerformanceOpt`](@ref)。デフォルトは`NoOpt()`。
  * `boundary`: グリッドの境界の処理方法。オプションは[`Remove`](@ref)または[`Wrap`](@ref)で、デフォルトは`Remove()`。
  * `cellsize`: ルールによってアクセスされるセルのサイズ。
  * `timestep`: 一部のルールに必要な固定タイムステップ。例：`Month(1)`または`1u"s"`。

その他：

  * `simdata`: [`SimData`](@ref)オブジェクト。シミュレーション間で保持することで、重要な場合にメモリ割り当てを少し減らすことができます。
