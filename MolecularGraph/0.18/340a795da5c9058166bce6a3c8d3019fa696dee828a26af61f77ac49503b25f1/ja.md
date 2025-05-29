```
smilestomol(smiles::AbstractString) -> GraphMol{SmilesAtom,SmilesBond}
```

SMILES文字列を`GraphMol`オブジェクトに解析します。

このライブラリのSMILESの構文は、Daylight SMILESとOpenSMILESの両方に従っています。

# 参考文献

1. OpenSMILES仕様 http://opensmiles.org/spec/open-smiles.html
2. Daylightチュートリアル https://www.daylight.com/dayhtml_tutorials/index.html
