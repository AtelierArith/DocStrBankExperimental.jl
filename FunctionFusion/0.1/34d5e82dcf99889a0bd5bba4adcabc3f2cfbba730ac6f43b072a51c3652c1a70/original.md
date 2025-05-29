```
# 1 
@provider function name(arg::Artifact, ...)::Artifact
          ...
end

# 2
@provider name(arg::Artifact, ...)::Artifact = x

# 2
@provider name(Artifact,...)::Artifact

# 3
@provider alias = name(Artifact, ...)::Artifact
```

Declares a provider with given inputs and output. All inputs + output must be unique artifacts.

3 versions of the syntax are supported: 1 and 2 - function definitions 3 - declare existing function as provider 4 - make an alias to existing function and declare it as a provider
