# MailChimp API

Supports v3 of the Mailchimp API

## Installation
```
# Clone the repo and save as 'mailchimp'
git clone git@github.com:wouterhendriks/webhare-mailchimp.git "$(wh getdatadir)installedmodules/mailchimp"
```

## Example usage:
```
<?wh

LOADLIB "mod::mailchimp/lib/api.whlib";

OBJECT api := NEW MailChimpAPI("... your API key ...");
api->debug := TRUE;

RECORD data :=
  [ email_address := "info@example.com"
  , merge_fields :=
    [ fname := "First name"
    , lname := "Last name"
    , address :=
      [ addr1 := "Address line 1"
      //, addr2 := "Address line 2"
      , city := "Enschede"
      , zip := "1234 AB"
      //, state := "..."
      ]
    , phone := "0031612345678"
    ]
  ];

abort(api->AddListMember("... your list id ...", data));
```

Note that using e-mail address like `info+3410505@example.com` are not accepted by Mailchimp and will result in errors.
