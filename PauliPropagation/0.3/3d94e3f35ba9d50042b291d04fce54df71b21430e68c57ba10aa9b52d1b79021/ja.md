```
tfitrottercircuit(nqubits::Integer, nlayers::Integer; topology=nothing, start_with_ZZ=true)
```

横場イジングハミルトニアンのトロッター化に対応する回路を作成します。トポロジーは、量子ビットインデックスのペアのリストとして指定できます。トポロジーが指定されていない場合、レンガ職人のトポロジーが使用されます。`start_with_ZZ`が`true`に設定されている場合、回路はZZゲートの層から始まり、そうでない場合はXゲートの層から始まります。これは初期状態に応じて重要です。
