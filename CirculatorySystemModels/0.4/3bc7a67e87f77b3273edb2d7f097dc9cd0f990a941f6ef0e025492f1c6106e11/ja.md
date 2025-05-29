`ShiPulmonaryLoop(; name, PAS.C, PAS.R, PAS.L, PAT.C, PAT.R, PAT.L, PAR.R, PCP.R, PVN.C, PVN.R)`

シーによって書かれた系統ループを実装します [Shi]。

パラメータは cm, g, s システムで表されます。圧力は mmHg で、体積は ml で、流量は cm^3/s (ml/s) で表されます。

名前付きパラメータ：

`PAS__C`:   動脈洞のコンプライアンス (ml/mmHg)

`PAS__R`:   動脈洞の抵抗 (mmHg*s/ml)

`PAS__L`:   動脈洞のインダクタンス (mmHg*s^2/ml)

`PAT__C`:   動脈のコンプライアンス (ml/mmHg)

`PAT__R`:   動脈の抵抗 (mmHg*s/ml)

`PAT__L`:   動脈のインダクタンス (mmHg*s^2/ml)

`PAR__R`:   小動脈の抵抗 (mmHg*s/ml)

`PCP__R`:   毛細血管の抵抗 (mmHg*s/ml)

`PVN__C`:   静脈のコンプライアンス (ml/mmHg)

`PVN__R`:   静脈の抵抗 (mmHg*s/ml)
