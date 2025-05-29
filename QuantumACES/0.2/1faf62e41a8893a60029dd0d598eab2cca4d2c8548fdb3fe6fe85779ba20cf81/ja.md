QuantumACESは、平均回路固有値サンプリング（ACES）を用いた安定器回路のスケーラブルで高性能なパウリノイズ特性評価実験の設計とシミュレーションのためのパッケージです。量子誤り訂正とフォールトトレラント回路の文脈に焦点を当て、特にトポロジカル量子誤り訂正コードのシンドローム抽出回路に注目しています。安定器回路のシミュレーションには[Stim](https://github.com/quantumlib/Stim)を、デコーディングには[PyMatching](https://github.com/oscarhiggott/PyMatching)と[BeliefMatching](https://github.com/oscarhiggott/BeliefMatching)を、量子デバイスでの実装には[Qiskit](https://github.com/Qiskit/qiskit)をインターフェースしています。

このパッケージで使用される手法は、[arXiv:2404.06545](https://arxiv.org/abs/2404.06545)および[arXiv:2502.21044](https://arxiv.org/abs/2502.21044)に基づいており、[arXiv:2108.05803](https://arxiv.org/abs/2108.05803)で紹介された元のACESプロトコルに基づいています。

[arXiv:2404.06545](https://arxiv.org/abs/2404.06545)のコードは、[scalable_aces](https://github.com/evanhockings/QuantumACES.jl/tree/scalable_aces)ブランチの`scalable_aces`フォルダーにあります。

[arXiv:2502.21044](https://arxiv.org/abs/2502.21044)のコードは、[aces_decoding](https://github.com/evanhockings/QuantumACES.jl/tree/aces_decoding)ブランチの`aces_decoding`フォルダーにあります。
