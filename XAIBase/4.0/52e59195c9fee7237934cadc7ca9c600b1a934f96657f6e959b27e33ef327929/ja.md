すべてのXAIメソッドの抽象スーパタイプ。

すべてのXAIメソッドは、`Explanation`を返す呼び出し可能なタイプであることが期待されています：

```julia
(method::AbstractXAIMethod)(input, output_selector::AbstractOutputSelector)
```

この関数が実装されている場合、XAIBaseは、VisionHeatmaps.jlまたはTextHeatmaps.jlのいずれかをロードすることによって、`analyze`機能と`heatmap`機能を提供します。
