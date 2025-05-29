```
addnode!(sim::Simulation, nodepos::Pos3D, protocol, args...; relpos=[(0,0,0)], ochannels=1)
```

指定された `protocol` を介してアクセス可能な位置 `nodepos` にシミュレーションノードを追加します。 `args` はプロトコルの引数で、プロトコルのコンストラクタに渡されます。ノードが複数のトランスデューサ/ハイドロフォンをサポートしている場合、それらの相対位置（`nodepos` に対する）は `relpos` の位置ベクトルとして提供する必要があります。 `ochannels` はノードがサポートする送信機の数です。チャネル `1:ochannels` は送信と受信が可能であると想定されており、チャネル `ochannels+1:length(relpos)` は受信専用チャネルであると想定されています。
