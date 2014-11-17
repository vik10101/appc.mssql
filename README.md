# MSSQL Connector

This is a API Builder connector to MSSQL.

> This software is pre-release and not yet ready for usage.  Please don't use this just yet while we're working through testing and finishing it up. Once it's ready, we'll make an announcement about it.

To install:

```bash
$ appc install connector/appc.mssql --save
```

Use in your application:

```javascript
var MSSQLConnector = require('appc.mssql'),
	connector = new MSSQLConnector({
		server: 'localhost',
		port: 1433,
		user: '',
		password: '',
		database: 'test',
		options: {
			encrypt: true
		}
	});
```

By default we use `localhost`, and empty username and password.

However, you must set a database.

Now reference the connector in your model.

```javascript
var Account = APIBuilder.createModel('Account',{
	fields: {
		Name: {type:'string', required: true, validator: /[a-zA-Z]{3,}/ }
	},
	connector: 'appc.mssql'
});
```

If you want to map a specific model to a specific sobject name, use metadata.  For example, to map the `account` model to the table named `accounts`, set it such as:

```javascript
var Account = APIBuilder.createModel('account',{
	fields: {
		Name: {type:'string', required: false, validator: /[a-zA-Z]{3,}/ }
	},
	connector: 'appc.mssql',
	metadata: {
		mssql: {
			table: 'accounts'
		}
	}
});
```

The tests will automatically create their own table named "TEST_Post".

# License

This source code is licensed as part of the Appcelerator Enterprise Platform and subject to the End User License Agreement and Enterprise License and Ordering Agreement. Copyright (c) 2014 by Appcelerator, Inc. All Rights Reserved. This source code is Proprietary and Confidential to Appcelerator, Inc.
