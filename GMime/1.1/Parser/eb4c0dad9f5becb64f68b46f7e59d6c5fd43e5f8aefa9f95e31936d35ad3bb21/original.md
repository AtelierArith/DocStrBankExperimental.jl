```
Email
```

Email structure with metadata and attachments.

## Fields

  * `from::Union{Nothing,Vector{String}}`: Vector of the email sender(s) addresses.
  * `to::Union{Nothing,Vector{String}}`: Vector of the email recipient(s) addresses.
  * `date::Union{Nothing,DateTime}`: The date and time the email was sent.
  * `text_body::Vector{UInt8}`: Binary data of the email's text body.
  * `attachments::Vector{EmailAttachment}`: Vector of the email attachments with metadata.
