```
rename(oldtree::AbstractTree, 
	oldtonew::Dict{<:AbstractString,<:AbstractString}
```

古い名前から新しい名前へのマッピングによって、`oldtree`からそれぞれ名前が変更された新しいツリーを作成します。具体的には、名前が空のノードはそのまま残ります。
