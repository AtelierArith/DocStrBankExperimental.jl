```julia
encrypt_playfair(plaintext, key::Array{Char, 2}; stripped::Bool = false, combined::AbstractPair{Char, Char} = ('I', 'J'))
```

与えられた平文をプレイフェア暗号に従って暗号化します。`combined`タプルの2番目のエントリがキーに存在する場合、エラーをスローします。

オプションのパラメータ：

`stripped=false`。trueに設定すると、`encrypt_playfair`は平文を大文字に変換せず、句読点を削除し、キーで結合されるべき文字を結合するのをスキップします。`combined=('I', 'J')`は、テキストで結合されるべき文字を示します。これらの2つのうちの最初のものだけが`encrypt_playfair`の出力に存在することができます。

---

### 例

```julia
julia> encrypt_playfair("Hello, World!", "playfair example")
"DMYRANVQCRGE"

julia> arr = ['P' 'L' 'A' 'Y' 'F'; 'I' 'R' 'E' 'X' 'M'; 'B' 'C' 'D' 'G' 'H'; 'K' 'N' 'O' 'Q' 'S'; 'T' 'U' 'V' 'W' 'Z'];

julia> encrypt_playfair("Hello, World!", arr) # 明示的に指定されたキー平方を使用して同じテキストを暗号化
"DMYRANVQCRGE"

julia> encrypt_playfair("IJXYZA", "PLAYFIREXM", combined=('I', 'J')) # 結合されるべき2文字をオプションで指定（デフォルトは'I','J'）
"RMRMFWYE"

julia> encrypt_playfair("IJXYZA", "PLAYFIREXM", combined=('X', 'Z'))
"BSGXEY"
```
