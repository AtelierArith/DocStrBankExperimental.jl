String value to be used as the sampler argument.

The specified value will only be used if OTEL*TRACES*SAMPLER is set. Each Sampler type defines its own expected input, if any. Invalid or unrecognized input MUST be logged and MUST be otherwise ignored, i.e. the SDK MUST behave as if OTEL*TRACES*SAMPLER_ARG is not set.
