```
JLLBuildInfo
```

JLL内のすべてのプラットフォーム固有の情報を表す構造体です。この構造体は本質的に`BinaryBuilder2`の`BuildResult/ExtractResult`構造体の蒸留ですが、2つのパッケージの間の分離を維持し、非BinaryBuilder2ユーザーが必要に応じてこのパッケージを利用しやすくするために異なっています。
