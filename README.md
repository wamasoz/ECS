# ECS
## Synopsis

zUID is a cloud enabled service in the z/OS environment that generates a unique identifier using a specialized patent-pending algorithm. It is guaranteed to generate 100% unique identifiers until the year 34,000 without requiring a database system to manage.

Service returns the UID in 3 different hex formats, plain, GUID and ESS.
- plain:	32 bytes, 1234567890abcdef1234567890abcdef
- ESS:		34 bytes, 12345678-90abcdef12345678-90abcdef
- GUID:		36 bytes, 12345678-90ab-cdef-1234-567890abcdef

No authorization is needed for this service.


## Code Example

In each of the examples the @path@ variable is defined by the team that sets up the zUID service and the hostname:port values are all site specific.

### curl:
	curl -X GET "http://hostname:port@path@?OPTIONS(FORMAT=GUID)"
	
### COBOL CICS:
	Refer to readme_howto_COBOL
	
### standard browser (Chrome, IE, Safri):
	Request a "plain" UID from the service.
	http://hostname:port@path@
	
	Request a "ESS" UID from the service.
	http://hostname:port@path@?OPTIONS(FORMAT=ESS)
	
	Request a "GUID" UID from the service.
	http://hostname:port@path@?OPTIONS(FORMAT=GUID)
	
### Javascript:
	var svc = new XMLHttpRequest();
	var url = "http://hostname:port@path@?OPTIONS(FORMAT=GUID)";
	svc.open( "GET", url, false );
	svc.send( null );
	alert( "zUID response=" + svc.responseText );
    
    
## Motivation

Provide a 100% unique UID for the next 32,000 years regardless of growth without using a database system to manage the values.


## Installation

Refer to the installation instructions for complete setup in the z/OS environment.
http://install.zuid/...


## API Reference

	http://hostname:port@path@
	http://hostname:port@path@?OPTIONS(FORMAT=PLAIN)
	http://hostname:port@path@?OPTIONS(FORMAT=ESS)
	http://hostname:port@path@?OPTIONS(FORMAT=GUID)
	
	No additional HTTP headers used by this service.


## Contributors

###Randy Frerking	Walmart Stores Inc.
###Rich Jackson		Walmart Stores Inc.

## License

A short snippet describing the license (MIT, Apache, etc.)
