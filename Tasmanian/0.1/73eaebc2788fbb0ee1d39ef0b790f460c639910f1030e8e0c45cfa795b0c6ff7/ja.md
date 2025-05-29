```
estimateAnisotropicCoefficients(tsg::TasmanianSG, type, output)
```

は、現在ロードされているポイントのセットから異方性係数の推定値を返します。マニュアルを参照してください。

type: 使用する推定値を識別する文字列（マニュアルを参照）        推奨: 'iptotal'   'ipcurved'

output: int（使用する出力を示す）      精緻化のために使用する出力を選択します      シーケンスグリッドは、すべての出力を示すために -1 を受け入れます

getNumDimensions() の長さのベクトルを返します。 または 2*getNumDimensions()         最初の getNumDimensions() エントリのセットは xi 係数に対応し、          2 番目の getNumDimensions() エントリのセットは eta 係数に対応します。
