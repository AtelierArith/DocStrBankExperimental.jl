```
SeisRadon_fx(In,Par,itype);
```

RADON_FX: f-x、tau-p の前方および随伴ラドン変換の演算子で、線形または放物線ラドン変換を計算します。 IN    ラドン係数 itype =  1 の場合（前方変換）  In(np,nt)       CMP ギャザー         itype = -1 の場合（随伴変換）  In(nh,nt)

OUT   CMP ギャザー         itype =  1 の場合（前方変換）  Out(nh,nt)       ラドン係数  itype = -1 の場合（随伴変換）  Out(np,nt)

# パラメータ

  * `Par.h`: nh オフセットを含むベクトル
  * `Par.p`: itype='parab' の場合、遠方オフセット (s) で正規化された np 曲率を含むベクトル
  * `Par.p`: itype='linear' の場合、s/m での np 傾きを含むベクトル
  * `Par.dt`: サンプリング間隔
  * `Par.f`: BP 演算子の周波数コーナー - これはゼロ位相のウェーブレットのように機能します。
  * `Par.transf`:'parab', 'linear'

itype =  1  :  前方 itype = -1  :  随伴
