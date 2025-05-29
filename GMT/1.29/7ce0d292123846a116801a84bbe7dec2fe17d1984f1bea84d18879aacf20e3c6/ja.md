```
gmtbegin(name::String=""; fmt)
```

GMTセッションをモダンモード（GMT >= 6）で開始します。 'name' には拡張子の有無にかかわらず図の名前が含まれます。拡張子が使用されている場合（例："map.pdf"）、それは画像形式を選択するために使用されます。

代わりに、'fmt' を文字列またはシンボルとして使用して形式（ps、pdf、png、PNG、tif、jpg、eps）を指定できます。

デフォルトでは、name="GMTplot" および fmt="ps" です。
