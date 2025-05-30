```
set_section(chains::Chains, namemap)
```

提供された`namemap`パラメータ名のマッピングを使用して、`chains`から新しい`Chains`オブジェクトを作成します。

両方のチェーンは同じ基礎データを共有します。チェーン内で未割り当てのパラメータは、`:parameters`セクションに配置されます。
