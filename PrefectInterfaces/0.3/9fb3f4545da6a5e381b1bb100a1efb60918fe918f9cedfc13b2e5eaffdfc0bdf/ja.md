```
S3BucketBlock(
    blockname, blocktype, bucket_name, bucket_folder
    , region_name, aws_access_key_id, aws_secret_access_key)
```

これは、prefect-aws統合におけるPrefect S3Bucketブロックに対応しています。添付された関数：

```
read_path("path/to/object.csv")
write_path("path/to/object.csv", df::AbstractDataFrame)
```

ブロックで定義された`s3:://bucket_name/bucket_folder/path/to/object.csv`から相対的なキーでDataFrame csvオブジェクトを返すか、書き込みます。

# 例：

```julia
# Prefect DBサーバーから仮想の既存ブロックを取得

julia> s3block = PrefectBlock("s3-bucket/willowdata")
S3BucketBlock("s3-bucket/willowdata", "s3-bucket", "willowdata", "data-folder/dev", "us-west-2"
, "AKIAEXAMPLEXXX", ####Secret####, ...)

julia> df = s3block.block.read_path("extracts/csv/dataset=test_table/rundate=2023-05-25/data.csv");

julia> s3block.block.write_path("testfolder/xanadu-test.csv", df)
p"s3://willowdata/data-folder/dev/testfolder/xanadu-test.csv"
```
