```
XPRS_CPUPLATFORM
```

ニュートンバリア: バリアが最適化されたコードを実行するために使用するAMD、Intel x86またはARMベクトル化命令セットを選択します。(整数)

AMD / Intel x86プラットフォームではSSE2、AVXおよびAVX2命令セットがサポートされており、ARMプラットフォームではNEONアーキテクチャ拡張を有効にできます。

デフォルト値: `-2`、CPUがサポートしている場合はAVX2命令を使用

値: -2 : サポートされている最高の[Generic, SSE2, AVXまたはAVX2]。 -1 : サポートされている最高の解決パスに一貫したコード[Generic, SSE2またはAVX]。 0 : すべてのCPUと互換性のある一般的なコードを使用。 1 : SSE2 / NEON最適化コードを使用。 2 : AVX最適化コードを使用。 3 : AVX2最適化コードを使用。
