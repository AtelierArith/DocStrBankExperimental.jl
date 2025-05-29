```
@computation function something(...)
    return ...
end

@computation Contract(...) function something(daf::DafWriter, ...)
    return ...
end

@computation Contract(...) Contract(...) function something(
    first::DafReader/DafWriter, second::DafReader/DafWriter, ...
)
    return ...
end
```

関数を `Daf` 計算としてマークします。これには以下の効果があります：

  * 計算が呼び出されるときと完了するときに、`Daf` データが [`Contract`](@ref) を満たしていることを検証します（[`verify_input`](@ref) と [`verify_output`](@ref) を使用）。
  * グローバル変数に契約（ある場合）を保存します。これにより、ドキュメント文字列内で [`CONTRACT`](@ref) を展開することができ（単一契約の場合）、また [`CONTRACT1`](@ref) と [`CONTRACT2`](@ref) を展開することができます（デュアル契約の場合）。
  * 名前付き引数のデフォルト値を保存します。これにより、ドキュメント文字列内で [`DEFAULT`](@ref) を展開することができ、特にこれらのデフォルトが計算されたり、グローバル定数から読み取られたりする場合に便利です。
  * 関数の呼び出しをログに記録します（`@debug` を使用）、名前付き引数の実際の値を含めて（[`depict`](@ref) を使用）。

!!! note
    各 [`Contract`](@ref) パラメータ（ある場合）には、契約が適用される [`DafReader`](@ref) または [`DafWriter`](@ref) が必要です。これらのパラメータは、関数の最初の位置引数であるべきです。

