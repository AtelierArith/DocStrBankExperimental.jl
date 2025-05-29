```
functional_cartography(N::T, L::Dict{E,Int64}) where {T<:BinaryNetwork, E}
```

この関数は、モジュラリティ分析の出力（*すなわち* ネットワークとパーティション）を受け取り、すべての種がOlesen et al (2005)で定義された機能的役割に関連付けられた辞書を返します。最初の要素はモジュール内の次数zスコアであり、2番目は参加係数です。

#### 参考文献

Guimerà, R., Amaral, L.A.N., 2005. 複雑ネットワークの地図作成：モジュールと普遍的役割. Journal of Statistical Mechanics: Theory and Experiment 2005, P02001. https://doi.org/10.1088/1742-5468/2005/02/P02001

Guimerà, R., Nunes Amaral, L.A., 2005. 複雑な代謝ネットワークの機能的地図作成. Nature 433, 895–900. https://doi.org/10.1038/nature03288

Olesen, J.M., Bascompte, J., Dupont, Y.L., Jordano, P., 2007. 授粉ネットワークのモジュラリティ. Proceedings of the National Academy of Sciences 104, 19891–19896. https://doi.org/10.1073/pnas.0706375104
