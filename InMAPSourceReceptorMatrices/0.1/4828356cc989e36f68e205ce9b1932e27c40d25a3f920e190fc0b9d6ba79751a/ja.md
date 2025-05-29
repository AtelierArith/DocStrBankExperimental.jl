```
connect_to_isrm!(; region="us-east-2", creds = nothing, url="s3://inmap-model/isrm_v1.2.1.zarr/")
```

AWSに接続し、`zopen`（Zarr.jlから）を使用してINMAPソース受容体行列を開きます。
