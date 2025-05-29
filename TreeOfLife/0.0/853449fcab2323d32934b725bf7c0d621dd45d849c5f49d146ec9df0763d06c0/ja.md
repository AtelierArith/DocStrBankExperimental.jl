```
rename!(tree::Tree, 
	oldtonew::Dict{<:AbstractString,<:AbstractString}
```

古い名前から新しい名前へのマッピングによって、ツリーのノードをその場で名前変更します。具体的には、名前が空のノードはそのまま残ります。
