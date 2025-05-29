```
clear_worker_caches!(pool::AbstractWorkerPool)
```

プール内のワーカーのキャッシュ（キャッシュされた関数クロージャなど）をクリアします。

プールがワーカーキャッシングを行っていない場合は、何もしません。
