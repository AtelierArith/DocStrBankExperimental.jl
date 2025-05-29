```
getcoeff(psum::PauliSum, pstr::PauliString)
```

`PauliSum`内の`PauliString`の係数を取得します。`PauliSum`にPauli文字列が含まれていない場合は、デフォルトで0になります。`pstr`内の整数Pauli文字列が`psum`内の整数Pauli文字列と同じタイプである必要があります。
