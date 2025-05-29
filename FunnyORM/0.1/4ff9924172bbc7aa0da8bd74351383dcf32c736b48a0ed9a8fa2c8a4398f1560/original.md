AbstractModel is the base type for your models. You should not instantiate your model manually.

You get it with a:

  * query: `db[MyModel[conditions...]][idx]`
  * insertion: `MyModel(db)(kwargs)`
  * updating: `newmodel = db[oldmodel](update_kwargs...)` or `@update db[model] key1=val1 key2=val2 ...`
