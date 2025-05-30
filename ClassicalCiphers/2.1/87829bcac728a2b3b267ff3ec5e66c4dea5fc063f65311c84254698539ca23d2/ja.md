```julia
crack_vigenere(plaintext; keylength::Integer = 0)
```

与えられたテキストをヴィジュネル暗号で解読します。

`(導出された鍵, 復号化された平文)`を返します。

オプションのパラメータ: `keylength=0`: 鍵の長さが知られている場合、それを指定することで解決者に役立つかもしれません。0の場合、解決者は一致のインデックスを使用して鍵の長さを導出しようとします。

---

### 例

```julia
julia> crack_vigenere(str)
```
