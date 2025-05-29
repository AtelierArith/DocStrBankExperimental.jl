```
(service::JSONService)(
    operation::String, args::AbstractDict{String, <:Any}=Dict{String, Any}();
    aws_config::AbstractAWSConfig=aws_config
)
```

Perform a JSON request to AWS.

# Arguments

  * `operation::String`: Name of the operation to perform
  * `args::AbstractDict{String, <:Any}`: Additional arguments to be included in the request

# Keywords

  * `aws_config::AbstractAWSConfig`: AWSConfig containing credentials and other information for fulfilling the request, default value is the global configuration
  * `feature_set::FeatureSet`: Specifies opt-in functionality for this specific API call.

# Returns

  * `Tuple` or `Dict`: If `return_headers` is passed in through `args` a Tuple containing the headers and response will be returned, otherwise just a `Dict`
