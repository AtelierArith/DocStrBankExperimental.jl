```
G = ControlSystemsBase.feedback(loopgain::T; name)
```

フィードバック相互接続を形成します $G = L/(1+L)$

システム `G` は `input` および `output` コネクタを持つ新しいシステムになります。
