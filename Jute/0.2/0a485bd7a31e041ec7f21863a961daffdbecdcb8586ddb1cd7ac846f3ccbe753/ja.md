```
@global_fixture [option=val ...] <name> begin ... end
@global_fixture [option=val ...] <name> for x in fx1, (y, z) in fx2 ... end
```

グローバルフィクスチャを作成します（それを使用するすべてのテストケースの前に一度設定され、終了後に解体されるフィクスチャ）。

本体には、単一の値を生成する[`@produce`](@ref)への単一の呼び出しが含まれている必要があります。

`for`ループ内のイテラブルは、フィクスチャ（グローバルの定数のみ）、イテラブルオブジェクト、またはフィクスチャをパラメータ化するために使用される2つのイテラブルのペアのいずれかです。

利用可能なオプション：

`instant_teardown :: Bool`: `true`の場合、[`@produce`](@ref)の後のフィクスチャ本体の部分が即座に実行されます。

[`GlobalFixture`](@ref)オブジェクトを返します。
