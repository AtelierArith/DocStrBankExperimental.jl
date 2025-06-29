```
@cm_component component_name(; props...) = "file_name.md"
```

マークダウンファイルから新しい `@component` 定義を作成します。ファイルの内容を解析してレンダリングするために `CommonMark.jl` パッケージが使用されるため、この機能はパッケージ拡張メカニズムを介して提供されるため、そのパッケージは依存関係としてインストールされている必要があります。

通常の `@component` と同様に、マークダウンコンポーネントに `props` を提供することができ、これらは任意の補間値で使用されます（補間のための `CommonMark` `$` 構文を使用）。

`Revise.jl` がアクティブで、`@cm_component` 定義を含むパッケージを追跡している場合、ソースマークダウンファイルへの更新が追跡され、コードの改訂を行うために `Revise` に渡されます。
