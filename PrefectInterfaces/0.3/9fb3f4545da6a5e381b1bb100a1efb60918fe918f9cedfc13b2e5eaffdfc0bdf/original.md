```
S3BucketBlock(
    blockname, blocktype, bucket_name, bucket_folder
    , region_name, aws_access_key_id, aws_secret_access_key)
```

Corresponds with the Prefect S3Bucket block in the prefect-aws integration. Attached functions:

```
read_path("path/to/object.csv")
write_path("path/to/object.csv", df::AbstractDataFrame)
```

Returns or writes a DataFrame csv object at a relative key from the block-defined `s3:://bucket_name/bucket_folder/path/to/object.csv`.

# Examples:

```julia
# pull hypothetical existing block from Prefect DB server

julia> s3block = PrefectBlock("s3-bucket/willowdata")
S3BucketBlock("s3-bucket/willowdata", "s3-bucket", "willowdata", "data-folder/dev", "us-west-2"
, "AKIAEXAMPLEXXX", ####Secret####, ...)

julia> df = s3block.block.read_path("extracts/csv/dataset=test_table/rundate=2023-05-25/data.csv");

julia> s3block.block.write_path("testfolder/xanadu-test.csv", df)
p"s3://willowdata/data-folder/dev/testfolder/xanadu-test.csv"
```
