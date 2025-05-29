Parsing Expression GrammarをマクロとJulia構文の乱用を通じて定義します。

  * ルール: `@rule name = expression`
  * 選択: 中置 `,`
  * シーケンス: 中置 `&`
  * 正の先読み: プレフィックス `+`
  * 負の先読み: プレフィックス `-`
  * オプション（0回または1回）: ポストフィックス `[:?]`（≡ `[0:1]`）

      * （[?]はJulia >= 1.0では機能しないことに注意してください。JuliaLang/julia#22712）
  * 0回以上: ポストフィックス `[*]`（≡ `[0:end]`）
  * 1回以上: ポストフィックス `[+]`（≡ `[1:end]`）
  * 正確に `m` 回: ポストフィックス `[m]`（≡ `[m:m]`）（ここでmは整数）
  * `m` 回から `n` 回まで（両端を含む）: ポストフィックス `[m:n]`
  * 最大 `n` 回: ポストフィックス `[0:n]`
  * 最小 `m` 回: ポストフィックス `[m:end]`
  * ターミナル: `r"regex"`, `"string"`

      * 追加の正規表現フラグ: `p` は句読点用で、マッチの後に空白（`\s*`）を食べます; `w` は単語用で、`p` を含意しますが、マッチ境界が単語境界（`\b`）であることを保証します; `h` は `p` と `w` を修正して、水平空白（`\h`）のみを食べます。セマンティクス関数に渡される値は、食べられた空白を除外します。
  * セマンティクス: `expression |> unary_function`（ParserCombinatorのように）

      * または `expression > nary_function` で引数を補間します。
      * セマンティクス関数から特別な単一値 `PEG.Failure()` を返すと、それに付随する構文表現が失敗します（タプルの代わりに `nothing` を返します）。セマンティクス関数から `nothing` を返すことは特別ではなく、タプルの最初の部分が `nothing` になるだけです。以下の構文関数のシグネチャを参照してください。

別の言い方をすれば：

```julia
using PEG
@rule grammar = "using PEG\n" & rule[*]
@rule rule = r"@rule"p & nonterminal & r"="p & choice
@rule choice = seq & (r","p & seq)[*]
@rule seq = item & (r"&"p & item)[*] & (r"\|?>"p & julia_function)[:?]
@rule item = lookahead , counted
@rule lookahead = r"\("p & (r"[+-]"p) & seq & r"\)"p
@rule counted = single & (count)[:?]
@rule count = range , r"\["p & (":?" , r"[\*\+]"p) & r"]"p
@rule range = r"\["p & integer & (r":"p & (integer , r"end"w))[:?] & r"]"p
@rule integer = r"\d+"w
@rule single = parens , terminal , nonterminal
@rule parens = r"\("p & choice & r"\)"p
@rule nonterminal = r"\pL\w+"w
@rule terminal = regex , string & r"\s*"
@rule regex = r"\br" & string & r"[himpswx]*\s*"
@rule string = r""(\\.|[^"])*""
@rule julia_function = # 演習として残します ;)
```

各ルールは次のシグネチャを持つ構文関数を定義します：

```julia
nonterminal(input::T, cache=PEG.Cache()) where T <: AbstractString
  ::Union{Nothing,Tuple{Any,SubString}}
```

戻り値の `Any` 部分は抽象構文木であり、`SubString` は解析された部分の後の残りの入力です。解析に失敗した場合、`nothing` が返されます。

このように定義されたルールを直接使用することもできますが、`parse_next(rule, input; whole=false)` または `parse_whole(rule, input)` を使用する方が便利かもしれません。詳細については、ドキュメントを参照してください。

`PEG.setdebug!()` を呼び出すと、解析中にデバッグ情報が印刷されます。再度オフにするには `PEG.setdebug!(false)` を呼び出します。
