```
ancestralreconstruction(net::HybridNetwork, Y::Vector, params::ParamsBM)
```

系統ネットワーク（`net`）の内部ノードにおける祖先（未観測）特性値の条件付き期待値と分散を計算します。これは、ネットワークの先端における特性の値（`Y`）と、特性進化に使用されるプロセスの既知のパラメータ（現在は固定されたルートのBMのみが機能します）を考慮します。

この関数は、プロセスのパラメータが既知であることを前提としています。より一般的な関数については、`ancestralreconstruction(obj::PhyloNetworkLinearModel[, X_n::Matrix])`を参照してください。
