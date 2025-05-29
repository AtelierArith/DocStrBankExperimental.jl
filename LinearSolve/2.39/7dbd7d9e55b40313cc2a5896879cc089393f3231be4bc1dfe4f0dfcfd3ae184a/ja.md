`KLUFactorization(;reuse_symbolic=true, check_pattern=true)`

疎行列のLU因子分解で、構造が「少ない」疎性パターンに特化しています。

!!! note
    デフォルトでは、SparseArrays.jlは効率のために記号因子分解をキャッシュするように実装されています。すなわち、`set_A`が使用される場合、新しい`A`は前の`A`と同じ疎性パターンを持つことが期待されます。このアルゴリズムをその仮定が成り立たない文脈で使用する場合は、`reuse_symbolic=false`に設定してください。

