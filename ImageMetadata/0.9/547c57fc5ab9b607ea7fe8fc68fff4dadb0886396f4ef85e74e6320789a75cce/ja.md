```
spatialproperties(img)
```

空間的に宣言されたプロパティの名前を含む文字列のベクトルを返します。これらのプロパティは「空間的」と見なされ、`permutedims`を呼び出す際に順序を変更する必要があります。このようにしてプロパティを宣言します：

```
img[:spatialproperties] = [:spacedirections]
```
