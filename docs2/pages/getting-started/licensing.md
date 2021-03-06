# Licensing

## Evaluation Period
You can evaluate our library for several months before purchasing it.

The trial period stops at the end of the month. When you receive a license expiration error, download the latest version which will automatically extend your trial period.

You can also purchase the library [here](/pricing)

Upon purchase, you will receive a license name and a license key.

## Setup License from config file
The license name and key can be directly added in the app.config or web.config file in the appSettings section.


```csharp
<appSettings>
	<add key="Z_BulkOperations_LicenseName" value="[licenseName]"/>
	<add key="Z_BulkOperations_LicenseKey" value="[licenseKey]"/>
</appSettings>
```

## Setup License from code
You can also set the license name and key directly in the code.


```csharp
// using Z.BulkOperations; // Don't forget to include this.

string licenseName = //... PRO license name
string licenseKey = //... PRO license key

Z.BulkOperations.LicenseManager.AddLicense(licenseName, licenseKey);
```

### Recommendation
- Use the config file to store your license name and license key.
- **Web App:** Use Application_Start in global.asax to activate your license.
- **WinForm App:** Use the main thread method to activate your license.
- **Win Service:** Use the OnStart method to activate your license

> The AddLicense must be set before the first call to the library. Otherwise, you will start the evaluation period

## How can I check if my license is valid?
The validate method allow you to know whether your license is valid or not.

```csharp
// CHECK for default provider (SQL Server)
string licenseErrorMessage;
if (!Z.BulkOperations.LicenseManager.LicenseManager.ValidateLicense(out licenseErrorMessage))
{
    throw new Exception(licenseErrorMessage);
}

// CHECK for a specific provider
string licenseErrorMessage;
if (!Z.BulkOperations.LicenseManager.LicenseManager.ValidateLicense(out licenseErrorMessage, ProviderType.MySql))
{
   throw new Exception(licenseErrorMessage);
}
```
