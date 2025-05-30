```julia
encrypt_hill(plaintext::AbstractString, key::AbstractArray{Integer, 2})
```

与えられた平文をヒル暗号に従って暗号化します。キーは行列（すなわち、二次元の `Array{Int}`）または文字列として与えることができます。

キーが文字列として与えられた場合、使用前に文字列は大文字に変換され、記号は削除されます。これは正方形の整数長であると仮定され、行列のエントリは左上から右上に、次に左上から右上に、そして下に向かって左から右に埋められます。文字列が正方形の整数長でない場合、エラーがスローされます。

行列は26での逆行列でなければなりません。そうでない場合、エラーがスローされます。

---

### 例

```julia
julia> encrypt_hill("Hello, World!", [1 2; 5 7]) # 行列 `[1 2; 5 7]` のヒルキーで "Hello, World!" を暗号化
"PHHRGUWQRV"

julia> encrypt_hill("Hello, World!", "bcfh")
"PLHCGQWHRY"

julia> encrypt_hill("Hello", "bcfh") # 平文の長さがキー行列の次元の倍数でない場合、Xでパディングされます
"PLHCIX"
```
