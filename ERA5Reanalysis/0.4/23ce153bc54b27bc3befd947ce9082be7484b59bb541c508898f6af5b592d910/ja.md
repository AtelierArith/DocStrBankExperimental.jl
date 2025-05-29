```
isSingle(
    ID :: AbstractString;
    throw :: Bool = true,
    dolog :: Bool = false
) -> tf :: Bool
```

ID `ID`を持つシングルレベル変数の情報を抽出します。このIDに対応するシングルレベル変数が存在しない場合、エラーがスローされます。

# 引数

  * `RegID` : シングルレベル変数を識別するために使用されるキーワードID。IDが無効な場合（つまり、使用されていない場合）、エラーがスローされます。
  * `throw` : `true`の場合、`RegID`が有効なシングルレベル変数識別子でないときに、Boolean `tf`を返す代わりにエラーをスローします。
  * `dolog` : `true`の場合、結果とともに画面にログを返します。

# 戻り値

  * `tf` : 真 / 偽
