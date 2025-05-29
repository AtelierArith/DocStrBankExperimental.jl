```
aws_http_proxy_options_init_from_config(options, config)
```

Initializes non-persistent http proxy options from a persistent http proxy configuration

# Arguments

  * `options`: http proxy options to initialize
  * `config`: the http proxy config to use as an initialization source

### Prototype

```c
void aws_http_proxy_options_init_from_config( struct aws_http_proxy_options *options, const struct aws_http_proxy_config *config);
```
