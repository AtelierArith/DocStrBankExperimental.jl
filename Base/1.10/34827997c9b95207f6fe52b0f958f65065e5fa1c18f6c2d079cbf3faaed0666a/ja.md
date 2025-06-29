```
code_lowered(f, types; generated=true, debuginfo=:default)
```

与えられたジェネリック関数と型シグネチャに一致するメソッドの低下した形式（IR）の配列を返します。

`generated` が `false` の場合、返される `CodeInfo` インスタンスはフォールバック実装に対応します。フォールバック実装が存在しない場合はエラーがスローされます。`generated` が `true` の場合、これらの `CodeInfo` インスタンスは、ジェネレーターを展開することによって得られるメソッド本体に対応します。

キーワード `debuginfo` は、出力に存在するコードメタデータの量を制御します。

`generated` が `true` の場合、`types` がリーフ型でないとき、対応するメソッドのいずれかが `@generated` メソッドであるとエラーがスローされることに注意してください。
