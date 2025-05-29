price_history(ticker, freq, start::DateTime=now()-Day(1), stop::DateTime=now())

`start`から`stop`までの`interval`ティックの価格履歴を取得します。

有効な頻度: 分: 1*, 5, 10, 15, 30
