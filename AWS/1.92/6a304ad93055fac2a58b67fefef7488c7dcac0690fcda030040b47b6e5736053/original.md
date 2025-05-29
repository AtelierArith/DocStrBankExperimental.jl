```
(service::RestXMLService)(
    request_method::String, request_uri::String, args::AbstractDict{String, <:Any}=Dict{String, String}();
    aws_config::AbstractAWSConfig=aws_config
)
```

Perform a RestXML request to AWS.

# Arguments

  * `request_method::String`: RESTful request type, e.g.: `GET`, `HEAD`, `PUT`, etc.
  * `request_uri::String`: AWS URI for the endpoint
  * `args::AbstractDict{String, <:Any}`: Additional arguments to be included in the request

# Keywords

  * `aws_config::AbstractAWSConfig`: AWSConfig containing credentials and other information for fulfilling the request, default value is the global configuration
  * `feature_set::FeatureSet`: Specifies opt-in functionality for this specific API call.

# Returns

  * `Tuple` or `Dict`: If `return_headers` is passed in through `args` a Tuple containing the headers and response will be returned, otherwise just a `Dict`
