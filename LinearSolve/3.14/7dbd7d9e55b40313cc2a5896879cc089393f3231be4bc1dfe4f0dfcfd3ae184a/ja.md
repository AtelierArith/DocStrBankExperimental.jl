`KLUFactorization(;reuse_symbolic=true, check_pattern=true)`

疎行列の「構造が少ない」スパースLU因子分解の高速化。

!!! note
    デフォルトでは、SparseArrays.jlは効率のためにシンボリック因子分解をキャッシュするように実装されています。すなわち、`set_A`が使用される場合、新しい`A`は前の`A`と同じスパースパターンを持つことが期待されます。このアルゴリズムをその仮定が成り立たない文脈で使用する場合は、`reuse_symbolic=false`に設定してください。

