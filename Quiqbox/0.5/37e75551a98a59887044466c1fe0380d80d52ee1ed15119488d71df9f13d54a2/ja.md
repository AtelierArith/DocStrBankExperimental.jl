```
genBasisFuncText(bf::FloatingGTBasisFuncs; 
                 norm::Real=1.0, printCenter::Bool=true, roundDigits::Int=-1) -> String
```

`FloatingGTBasisFuncs`のテキストを生成します。`norm`は追加の正規化係数です。`printCenter`が`true`の場合、中心座標が出力`String`の最初の行に追加されます。`roundDigits`は`bf`内のパラメータの丸め桁数を指定します。負の値に設定された場合、丸めは行われません。
