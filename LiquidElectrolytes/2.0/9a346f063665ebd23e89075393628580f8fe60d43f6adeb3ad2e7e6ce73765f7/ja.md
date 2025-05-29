```
μex_flux!(f,dϕ,ck,cl,γk,γl,electrolyte; evelo=0.0)
```

過剰化学ポテンシャル（セダン）上向きフラックス、修正されたシャーフェッター・グマルスキームに基づく。詳細はGaudeul/Fuhrmann 2022を参照。

明らかに最初にYu, ZhipingとDutton, Robertによって記述された、SEDAN III、www-tcad.stanford.edu/tcad/programs/sedan3.html

また、198?年のFortranコードは、https://web.archive.org/web/20210518233152/http://www-tcad.stanford.edu/tcad/programs/oldftpable.htmlから入手可能。

検証計算は論文に記載されている。
