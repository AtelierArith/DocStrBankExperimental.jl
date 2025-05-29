```julia
complete(
    sys::ModelingToolkit.AbstractSystem;
    split,
    flatten,
    add_initial_parameters
) -> Any

```

システムを完了としてマークします。完了したシステムは、定義/修正が完了し、構造解析やその他の変換の準備が整ったシステムです。これにより、システムのグローバルな構造を知る必要がある分析や最適化を実行できるようになります。

注意すべき特性の1つは、システムが完了している場合、システムはそのサブシステムや変数の名前空間をもはや持たないということです。すなわち、`isequal(complete(sys).v.i, v.i)`となります。
