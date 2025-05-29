[Yao.jl](https://github.com/QuantumBFS/Yao.jl) バックエンドは、[Classical simulation of noninteracting-fermion quantum circuits](https://arxiv.org/abs/quant-ph/0108010) および [Disorder-assisted error correction in Majorana chains](https://arxiv.org/abs/1108.3845) に基づいて、フェルミオン線形光学 (FLO) 回路を効率的にシミュレートします。FLO 回路は、非相互作用フェルミオンに密接に関連する量子回路のクラスであり、[YaoClifford.jl](https://github.com/QuantumBFS/YaoClifford.jl) で行われるように、クリフォード回路が効率的に古典的にシミュレートできるのと同様に、古典コンピュータ上で効率的にシミュレートできます。

`FLOYao.jl` の目標は、[FLO ゲート](https://quantumbfs.github.io/FLOYao.jl/stable/supported_gates/) および多項式時間と空間で効率的にシミュレート可能な他のプリミティブのみを使用して書かれた `Yao.jl` のコードがある場合、`AbstractArrayReg` を `MajoranaReg` に置き換えるだけで、同じコードでまったく同じシミュレーションを実行できるようにすることです。ただし、指数的に速くなります。

フェルミオン線形光学回路の簡単な紹介は、[Documentation](https://yaoquantum.org/FLOYao.jl/stable/background/) にあり、上記の2つの論文などでより詳細な紹介がされています。
