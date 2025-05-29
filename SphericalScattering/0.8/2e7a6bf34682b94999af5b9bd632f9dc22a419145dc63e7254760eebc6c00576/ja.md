```
DielectricSphereThinImpedanceLayer(
    radius    = error("missing argument `radius`"),
    thickness = error("missing argument `thickness` of the coating"),
    thinlayer = error("missing argument `thinlayer`"),
    filling   = error("missing argument `filling`")
)
```

薄インピーダンス層を持つ誘電体球のコンストラクタ。 このモデルでは、層内の変位場が放射方向のみに存在することが仮定されており、これは小さな厚さと低い導電率を必要とします。 詳細については、たとえば T. B. Jones 編著、"Models for layered spherical particles" を参照してください。Electromechanics of Particles, Cambridge: Cambridge University Press, 1995, pp. 227–235. doi: 10.1017/CBO9780511574498.012.
