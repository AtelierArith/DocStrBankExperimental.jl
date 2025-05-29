```
newlist,newtable = extract_ped(invp, pedlist ,idtable)
newlist          = extract_ped(invp, pedlist)
```

`invp`に基づいて`pedlist`内のコードを抽出します。ここで、`invp[oldid]=newid`は、`find_ped_order`のような関数で生成されます。オプションの`idtable`を使用すると、新しいテーブルも返されます。この関数は`newlist`内の動物にコードを再割り当てします。この動作は`permute_ped`に似ていますが、この関数は系譜の量を減らすことをサポートしています。
