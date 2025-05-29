`ShiSystemicLoop(; name, SAS.C, SAS.R, SAS.L, SAT.C, SAT.R, SAT.L, SAR.R, SCP.R, SVN.C, SVN.R)`

シーによって書かれた系統ループを実装します [Shi]。

パラメータはcm、g、sシステムで表されます。圧力はmmHgで、体積はmlで、流量はcm^3/s（ml/s）で表されます。

名前付きパラメータ：

`SAS_C`:   大動脈洞のコンプライアンス（ml/mmHg）

`SAS_R`:   大動脈洞の抵抗（mmHg*s/ml）

`SAS_L`:   大動脈洞のインダクタンス（mmHg*s^2/ml）

`SAT_C`:   動脈のコンプライアンス（ml/mmHg）

`SAT_R`:   動脈の抵抗（mmHg*s/ml）

`SAT_L`:   動脈のインダクタンス（mmHg*s^2/ml）

`SAR_R`:   小動脈の抵抗（mmHg*s/ml）

`SCP_R`:   毛細血管の抵抗（mmHg*s/ml）

`SVN_C`:   静脈のコンプライアンス（ml/mmHg）

`SVN_R`:   静脈の抵抗（mmHg*s/ml）
