# S3 Bucket Policy Examples and notes

## PreSigned URL
- aws s3 presign s3://mybucket/myobject  --expires-in 300



## Bucket with descriptive Sid names

{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "AllowPublicRead",
            "Effect": "Allow",
            "Principal": "*",
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::example-bucket/*"
        },
        {
            "Sid": "RestrictToUserUpload",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::123456789012:user/upload-user"
            },
            "Action": "s3:PutObject",
            "Resource": "arn:aws:s3:::example-bucket/*"
        },
        {
            "Sid": "therest",
            "Effect": "Deny",
            "Principal": "*",
            "Action": "s3:*",
            "Resource": "arn:aws:s3:::example-bucket/*"
        }
    ]
}

