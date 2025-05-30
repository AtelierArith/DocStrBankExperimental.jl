`UMFPACKFactorization(;reuse_symbolic=true, check_pattern=true)`

構造が「より多い」スパースパターンに特化した、高速なスパースマルチスレッドLU因子分解です。

!!! note
    デフォルトでは、SparseArrays.jlは効率のためにシンボリック因子分解をキャッシュするように実装されています。すなわち、`set_A`が使用される場合、新しい`A`は前の`A`と同じスパースパターンを持つことが期待されます。このアルゴリズムがその仮定が成り立たない文脈で使用される場合は、`reuse_symbolic=false`を設定してください。

