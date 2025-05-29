ContentSecurityPolicy.jl is library for working with Content Security Policy headers

Content-Security-Policy: default-src 'self'; script-src https://example.com

is the same as:

Content-Security-Policy:         connect-src 'self';         font-src 'self';         frame-src 'self';         img-src 'self';         manifest-src 'self';         media-src 'self';         object-src 'self';         script-src https://example.com;         style-src 'self';         worker-src 'self'

[Content-Security-Policy @ mdn](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/default-src)
