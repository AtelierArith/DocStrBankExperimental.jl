```
base64encode(writefunc, args...; context=nothing)
base64encode(args...; context=nothing)
```

[`write`](@ref)に似た関数`writefunc`を与えると、最初の引数としてI/Oストリームを受け取る`base64encode(writefunc, args...)`は、`writefunc`を呼び出して`args...`をbase64エンコードされた文字列に書き込み、その文字列を返します。`base64encode(args...)`は`base64encode(write, args...)`と同等で、標準の[`write`](@ref)関数を使用して引数をバイトに変換し、base64エンコードされた文字列を返します。

オプションのキーワード引数`context`は、`:key=>value`ペアまたは`IO`または[`IOContext`](@ref)オブジェクトに設定でき、その属性は`writefunc`または`write`に渡されるI/Oストリームに使用されます。

さらに[`base64decode`](@ref)も参照してください。
