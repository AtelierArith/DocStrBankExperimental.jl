```
write_mmcif(filename, atoms::AbstractVector{<:Atom}, [selection])
```

`atoms`に含まれる原子を`filename`にmmCIFファイルとして書き込みます。オプションの`selection`引数は、`atoms`内の原子のサブセットを選択するために使用できる文字列です。例えば、`write_mmcif(atoms, "test.cif", "name CA")`のように使用します。
