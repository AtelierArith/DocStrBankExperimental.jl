```
process!(model::Model)
```

構造モデルを処理します：ノードと要素の間にリンクを追加し、自由度の順序を決定し、荷重ベクトルP、Pfを生成し、グローバル剛性行列Sを組み立てます。
