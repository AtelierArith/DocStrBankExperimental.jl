```
get_value(l::LoopCategory, k::Dict{Symbol, V}, name::Symbol)
```

`k`の内容をシンボルとしてキー値として与えられた場合に、`name`の値を返します。この形式のメソッドは、子カテゴリオブジェクト名を親カテゴリのメンバーとして扱います。たとえば、`atom*site*aniso`が`atom_site`の子カテゴリである場合、`u*11`は`atom*site*aniso`と`atom*site`の両方に属します。リンクされたキーデータ名も同様に扱われます。
