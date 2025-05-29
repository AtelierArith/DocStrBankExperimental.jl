```
trixi_initialize_simulation(libelixir::Cstring)::Cint
trixi_initialize_simulation(libelixir::AbstractString)::Cint
```

`libelixir`ファイルに基づいて新しいシミュレーションを初期化し、対応する[`SimulationState`](@ref)へのハンドルを`Cint`（すなわち、通常のC `int`）として返します。

libelixirは、Trixi.jlの通常の「elixir」と同様の目的を持ち、Juliaコード内でシミュレーションセットアップを完全に定義します。主な違い（したがってlibelixirという名前）は、シミュレーションを直接実行するのではなく、完全なシミュレーションセットアップを持つ[`SimulationState`](@ref)を返す引数なしの関数`init_simstate()`を定義する必要があることです。`trixi_initialize_simulation`は、`SimulationState`オブジェクトを内部に保存し、この関数から返されたハンドルを介してlibtrixiへの後続の呼び出しで使用できるようにします。

便利なことに、Juliaから直接LibTrixi.jlを使用する際には、`libelixir`引数に通常の`String`を渡すこともできます。

!!! note "Libelixirの衛生と`init_simstate`"
    libelixirファイルは`Main`モジュールで評価されます。したがって、以前に定義された関数`init_simstate`は上書きされ、関数の外で定義された変数はJuliaプロセスのライフタイム全体にわたって存在します。


!!! warning "スレッド安全性"
    **この関数はスレッド安全ではありません。** libelixirファイルは`Main`モジュールで評価されるため、異なるスレッドから同時に`trixi_initialize_simulation`を呼び出すと未定義の動作を引き起こす可能性があります。

