```
Ecosystem{Part <: AbstractAbiotic} <:
   AbstractEcosystem{Part, SL, TR}
```

Ecosystemは種とその環境との相互作用に関する情報を保持します。種に関しては、個体数と位置、`abundances`、および特性情報、`spplist`、移動タイプ、`lookup`などのプロパティを保持します。環境に関しては、環境条件と利用可能な資源に関する情報を提供します、`abenv`。最後に、環境と種の特性との関係を示すスロット、`relationship`があります。
