```
noiseterm(P::ProjMPO,
          phi::ITensor,
          ortho::String)
```

"ノイズ項"または密度行列摂動ITensorを返します。これは、DMRG計算の収束を助けるためにPhys. Rev. B 72, 180403で提案されたものです。ITensor `phi`は、ProjMPO `P`によって作用されたMPSテンソルの収束積であり、`ortho`はDMRG計算のスイープ方向に応じて`"left"`または`"right"`の値を取ることができるStringです。
