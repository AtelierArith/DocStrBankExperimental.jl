```
parse_email(data::AbstractVector{UInt8}) -> Email
parse_email(data::AbstractString) -> Email
```

バイナリベクターまたは文字列 `data` を [Email](@ref) に解析します。

## 例

```julia
julia> email_string = """
       MIME-Version: 1.0
       Date: Fri, 7 Mar 1997 17:30:00 +0500
       Message-ID: <CAOU+8LMfxVaPMmigMQE2qTBLSbNdKQVps=Fi0S3X8LnfxT2xee@mail.email.com>
       Subject: Test Message
       From: Test User <username@example.com>
       To: Test User <username@example.com>
       Content-Type: multipart/alternative; boundary="000000000000dd23a50621ff39e8"

       --000000000000dd23a50621ff39e8
       Content-Type: text/plain; charset="UTF-8"

       Hello World!

       Best regards,
       Test User

       --000000000000dd23a50621ff39e8
       Content-Type: text/html; charset="UTF-8"

       <div dir="ltr">Hello World!<div><br></div><div>Best regards,</div><div>Test User</div></div>

       --000000000000dd23a50621ff39e8--
       """;

julia> email = parse_email(email_string)
📧 Email:
   📤 From: Test User <username@example.com>
   📥 To: Test User <username@example.com>
   🕒 Date: 1997-03-07T17:30:00
   📝 Text size: 39 bytes
   📨 No attachments.
```
