```
set_label(r::RemoteConcept{<:AbstractType},
    new_label_name::AbstractString)
```

この関数を使用すると、特定の型のラベルを設定できます。これにより、特定の型の名前を変更する機会が得られます。しかし、注意してください。これは、型が挿入されたデータによってインスタンス化されていない場合にのみ許可されます。
