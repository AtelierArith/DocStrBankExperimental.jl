```
update!(l::HashedLocator,curve,t,samples=l.lims)
```

`l.hash`を`curve`の`t`時点で`samples`を検索し、洗練させることで更新します。
