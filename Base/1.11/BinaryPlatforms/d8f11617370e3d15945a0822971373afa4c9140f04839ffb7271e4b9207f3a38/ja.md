```
select_platform(download_info::Dict, platform::AbstractPlatform = HostPlatform())
```

`download_info` 辞書がプラットフォームをいくつかの値にマッピングしている場合、`platform` に最もよく一致するキーの値を選択し、一致するものが見つからない場合は `nothing` を返します。

アーキテクチャ、libc、呼び出し ABI などのプラットフォーム属性はすべて正確に一致する必要がありますが、コンパイラ ABI のような属性は `nothing` のようにワイルドカードを含むことができ、これは任意のバージョンの GCC に一致します。
