##Organizations
```js
var partybot = require('partybot-http-client');
// Get all
partybot.organisations.getAll(function(err, response, body) {
	
	if(response.statusCode == constants.SUCCESS) {
		console.log(response.statusCode);
		console.log(body);
	}
	else {
		console.log(err);
	}

});
// Get Organisation with id
partybot.organisations.getWithId('57f3a270f760e4f8ad97eec4', function(err, response, body) {
	
	console.log(response.statusCode);
	console.log(body);
	console.log(err);

});
// Create
partybot.organisations.create({name: "New organisation"}, function(err, response, body) {
	
	console.log(response.statusCode);
	console.log(body);
	console.log(err);

});
// Update With Id
partybot.organisations.updateWithId('57f48fa9a9fd7b00113ba6b8', {name: "Update Organisation Name"}, function(err, response, body) {
	
	console.log(response.statusCode);
	console.log(body);
	console.log(err);

});
```
##Venues
```js
var organisationId = '57f3a270f760e4f8ad97eec4';

// Get All Venues in an Organisation
partybot.venues.getAllInOrganisation(organisationId, function(err, response, body) {
	
		console.log(response.statusCode);
		console.log(body);
		console.log(err);

});

var venueId = '57f380f17fb36ae92003647b';
// Get Venue with Organisation Id and Venue Id
partybot.venues.getWithOriganisationIdAndVenueId(organisationId, venueId, function(err, response, body) {
	
		console.log(response.statusCode);
		console.log(body);
		console.log(err);

});

// Get Venue directly
partybot.venues.getWithId(venueId, function(err, response, body) {
	
		console.log(response.statusCode);
		console.log(body);
		console.log(err);

});

// Create venue in a organisation
var params = {
	organisationId: organisationId,
	name: "Valkyrie",
	description: "Description of Valkyrie"
};

partybot.venues.create(params, function(err, response, body) {
	
	console.log(response.statusCode);
	console.log(body);
	console.log(err);

});

// Update Venue with Organisation Id and Venue Id

// Update Venue with Venue Id
```

###Events
```js

var organisationId = '57f3a270f760e4f8ad97eec4';
var venueId = '57f4681dbb6c3c23633eecc2';
var eventId = '57f4b1fda9fd7b00113ba6c8';

// Get All Events In Venue In Organisation
partybot.events.getAllEventsInVenueInOrganisation({organisationId: organisationId, venueId: venueId}, function(err, response, body) {
	console.log("Error: "+err);
	console.log("Status Code: "+response.statusCode);
	console.log("Body :"+JSON.stringify(body));
});

// Get Event In Venue In Organisation
partybot.events.getEventInVenueInOrganisation({organisationId: organisationId, venueId: venueId, eventId: eventId}, function(err, response, body) {
	console.log("Error: "+err);
	console.log("Status Code: "+response.statusCode);
	console.log("Body :"+JSON.stringify(body));
});
// Create Event

var createParams = {
		organisationId: organisationId,
		venueId: venueId,
		name: "Event",
		description: "Description of Event"
}

partybot.events.create(createParams, function(err, response, body) {
	console.log("Error: "+JSON.stringify(err));
	console.log("Status Code: "+response.statusCode);
	console.log("Body :"+JSON.stringify(body));
});
```

###Users
```js
var organisationId =  "57f3a270f760e4f8ad97eec4";
var userId = "57fdade284cd6200113dbed1";
var createUser = {
	organisationId: organisationId,
	name: { first: "JC", last: "Velasquez" },
	username: "scasro",
	password: "1234",
	permissions: ["su"],
	image: "https://media.licdn.com/mpr/mpr/shrinknp_200_200/p/2/000/1f2/03a/1a0ed21.jpg"
}

partybot.users.create(createUser, function(errors, response, body) {
	console.log("Errors: "+JSON.stringify(errors, null, 2) || null);
	console.log("Response status code: "+response.statusCode || null);
	console.log("Body: "+JSON.stringify(body) || null);
});

partybot.users.getAllInOrganisation({organisationId: organisationId}, function(errors, response, body) {
	console.log("Errors: "+JSON.stringify(errors, null, 2) || null);
	console.log("Response status code: "+response.statusCode || null);
	console.log("Body: "+JSON.stringify(body, null, 2) || null);
});
```
All update parameters are optional except organisationId and userId. Just put the keys that you want to update.
```js
var updateUser = {
	organisationId: organisationId,
	userId: userId,
	name: { first: "JC", last: "Velasquez" },
	username: "scasrzoo",
	password: "1234",
	permissions: ["su"],
	image: "https://media.licdn.com/mpr/mpr/shrinknp_200_200/p/2/000/1f2/03a/1a0ed21.jpg"
};

partybot.users.update(updateUser, function(errors, response, body) {
	console.log("Errors: "+JSON.stringify(errors, null, 2) || null);
	console.log("Response status code: "+response.statusCode || null);
	console.log("Body: "+JSON.stringify(body) || null);
});
```