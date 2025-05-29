```
scriptq(funct::AbstractString, runonce::AbstractString=""; label="", hint="", explanation="", placeholder="")
```

カスタムスクリプトで文字列の回答をチェックします

引数:

  * `funct`: シグネチャ `(str: string): boolean` の JavaScript 関数/クロージャの名前を表す文字列
  * `label`: フォーム要素のオプションのラベル
  * `hint`: ホバー時に表示されるオプションのプレーンテキストヒント
  * `explanation`: 不正な選択時に表示されるテキスト
  * `placeholder`: 入力ウィジェットが最初に描画されたときに表示されるテキスト

## 例

```javascript
// JavaScript で
function threshold(t) {
    return (input) => input >= t;
}
```

```julia
# Julia で
stringq("threshold(42)", label="大きな数")
```
