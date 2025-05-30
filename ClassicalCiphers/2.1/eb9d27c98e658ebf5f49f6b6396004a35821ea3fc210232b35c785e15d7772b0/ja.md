```julia
function encrypt_enigma(plaintext,
						rotors::Array{Integer, 1}, key::AbstractString;
						reflector_id='B', ring::AbstractString = "AAA",
						stecker = Tuple{Char, Char}[],
						skip_stecker_check = false)
```

与えられた平文をエニグマ（M3、陸軍版）に従って暗号化します。

引数は次の順序で指定されます：`plaintext, stecker, rotors, ring, key.`

平文は文字列であり、句読点は削除され、小文字に変換されます。ローターは配列で、例えば`[1,2,3]`のように、ローターの順序を示します。各エントリは1から5の間の異なる整数である必要があります。キーはローターの開始位置を示す3文字の文字列です。

オプション：

  * `reflector_id='B'`は、リフレクターA、B、またはCを使用するかどうかを設定します。

26文字の文字列として指定することもできます。

  * ステッカーは配列であるか、例えば`[('A','B'), ('D', 'E')]`のように、AとBが入れ替わり、DとEが入れ替わることを指定します。または、同じことを達成する文字列("ABDE")でも構いません。どの文字も1回以上現れてはいけません。
  * リングは文字列で、例えば"AAA"のように、各ローターに適用されるオフセットを示します。

"AAA"は、オフセットがないことを示します。この文字列は3文字でなければなりません。

  * `skip_stecker_check=false`は、`true`のときにステッカー設定の検証をスキップします。

---

### 例

```julia
julia> encrypt_enigma("AAA", [1,2,3], "ABC")
"CXT"

julia> encrypt_enigma("AAA", [1,2,3], "ABC", ring="AAA", reflector_id='B', stecker="") # 上記と同義
"CXT"

julia> encrypt_enigma("AAA", [1,2,3], "ABC", ring="AAA", reflector_id="YRUHQSLDPXNGOKMIEBFZCWVJAT", stecker="") # 上記と同義
"CXT"

julia> encrypt_enigma("AAA", [1,2,3], "ABC", ring="AAA", reflector_id='B', stecker=Tuple{Char, Char}[]) # 上記と同義
"CXT"
```
