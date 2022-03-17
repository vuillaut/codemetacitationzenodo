# OSSR metadata converters

Testing repository for metadata schemas.

[![](https://lucid.app/publicSegments/view/31f02de0-e92d-4839-b4df-8cbdcc3970a6/image.png)](https://lucid.app/lucidchart/f1b4a51a-8766-4bc1-915d-bf562c51123b/edit?invitationId=inv_32ce79ce-1a84-4848-8a74-4e724d9aff19&page=0_0#)


## `CITATION.cff` integration with Zenodo

Zenodo recognize automatically the `CITATION.cff` file inside the repository and converts it through the GitHub-Zenodo integration.
Resulting release: https://sandbox.zenodo.org/record/1035887


## Conversions

### To CodeMeta

#### Through Zenodo
After publication to Zenodo, one can export again to JSON-LD:
https://sandbox.zenodo.org/record/1035887/export/schemaorg_jsonld#.YjM-vxBKhB0

However, this is following the `schema.org` context and not the CodeMeta one.

#### cffconvert

```
cffconvert -i CITATION.cff -f codemeta -o codemeta_cffconvert.json
```

This works but here as well, the output schema is actually `schema.org` - even though it states CodeMeta schema.     
Opened issue: https://github.com/citation-file-format/cff-converter-python/issues/272

### To `.zenodo.json`

```
cffconvert -i CITATION.cff -f zenodo -o zenodo_cffconvert.json
```

Works.


### From CodeMeta

#### codemeta2cff

https://github.com/caltechlibrary/datatools

- Does not work with the output of `cffconvert`
- Works with the output of Zenodo
