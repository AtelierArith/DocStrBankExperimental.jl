```
FString(L, s::String)
```

Juliaの`String` `s`を`FString{L}`に変換します。`s`はASCII文字のみを含む必要があります。Fortranと同様に、文字列は目的の長さに達するためにスペースでパディングされるか、切り捨てられます。
