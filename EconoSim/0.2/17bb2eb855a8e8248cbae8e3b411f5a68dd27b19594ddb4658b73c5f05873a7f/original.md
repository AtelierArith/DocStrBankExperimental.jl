```
struct Balance
```

A balance sheet, including a history of transactions which led to the current state of the balance sheet.

# Properties

  * assets: the asset side of the balance sheet.
  * def*min*asset: the default lower bound for asset balance entries.
  * min*assets: minimum asset values. Used to validate transactions. Entries override def*min_asset.
  * liabilities: the liability side of the balance sheet.
  * def*min*liability: the default lower bound for liability balance entries.
  * min*liabilities:  minimum liability values. Used to validate transactions. Entries override def*min_liability.
  * log_transactions: flag indicating whether transactions are logged. Not logging transactions improves performance.
  * transactions: a chronological list of transaction tuples. Each tuple is constructed as follows: timestamp, entry type (asset or liability), balance entry, amount, new balance value, comment.
  * properties: a dict with user defined properties. If the key of the dict is a Symbol, the value can be retrieved/set by balance.symbol.
