空の回文オートマトンをキータイプ `T` で作成します。

回文オートマトン (PAM、または回文木とも呼ばれる) は、回文に関連する問題を解決するための非常に便利なデータ構造です。PAMの詳細な紹介は以下で見ることができます：

  * [Wikipedia: Palindrome Tree](https://en.wikipedia.org/wiki/Palindrome_tree)
  * [OI-Wiki: 回文树](https://oi-wiki.org/string/pam/)

オートマトンに新しい値を追加するには、単に `Base.push!` を使用します。

オートマトンの内部フィールドのゲッターが提供されており、以下のようなものがあります：

  * `children(pam)`: PAMの子辞書を取得します。
  * `nodecount(pam)`: PAMのノード数を取得します。
  * `lastnodeindex(pam)`: PAMの最後のノードのインデックスを取得します。
  * `len(pam, i)`: i 番目のノードの回文の長さを取得します。
  * `fail(pam, i)`: i 番目のノードの失敗ポインタを取得します。
  * `cnt(pam, i)`: i 番目のノードの頻度カウントを取得します。

# サンプル使用法

  * 最長回文部分文字列の長さを見つける

```jldoctest
function longest_palindromic_substring(s)
    pam = PalindromicAutomaton{Char}()
    hi = 0
    for ch in s
        push!(pam, ch)
        hi = max(hi, len(pam, lastnodeindex(pam)))
    end
    return hi
end

longest_palindromic_substring("ddabababacc")

# output

7
```
