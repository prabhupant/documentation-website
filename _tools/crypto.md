---
layout: default
title: Client side encryption
nav_order: 90
has_children: false
---


# Client side encryption



## Client side encryption API

To register an encryption enabled repository for <remote-store>.

### Request fields

| Field | Type | Description |
| :--- | :--- |:--- |
| `type` | String | Operation to be performed. Options include `remove`, ... Required. |
| `settings.bucket` | String | Path to the target distinguished name to be updated. Required. |
| `settings.region` | String | Path to the target distinguished name to be updated. Required. |
| `encrypted` | Boolean | Path to the target distinguished name to be updated. Required. |
| `crypto_settings.key_provider_name` | String | Path to the target distinguished name to be updated. Required. |


#### Example request

```json
PUT _snapshot/vikasvb-repository-test-1
{
  "type": "s3",
  "settings": {
    "bucket": "vikasvb-repository-test",
    "region": "us-west-2"
  },    
  "encrypted": true,
  "crypto_settings": {
      "key_provider_name": "first-mock-1",
      "key_provider_type": "sample-key-provider-extension",
      "settings": {
          "key-1": "sample value"
      }
  }
}
```
{% include copy-curl.html %}

#### Example response

```json
{
    "acknowledged": true
}
```

## External libraries

Software dependencies are mainly AWS v2 SDK. The following is a list of dependencies:

1. AWS encryption SDK (com.amazonaws:aws-encryption-sdk-java) - Some classes are modified to support encryption or decryption of partial content.
2. Bouncy castle (org.bouncycastle:bcprov-ext-jdk15on)  : Used by encryption SDK for core crypto ops.
3. Apache commons (org.apache.commons:commons-lang3) - Again used by encryption SDK for basic object validations.
4. Junit dependencies - For tests