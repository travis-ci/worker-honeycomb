tail: papertrail --group "04 - EC2 Workers" 'program:travis-worker' -f -j | jq -cr '.events[]|"hostname=" + .hostname + " " + .message' | honeytail --writekey=$(heroku config:get HONEYCOMB_WRITEKEY -a travis-api-staging) --dataset='worker' --parser=keyval --keyval.timefield=time --keyval.filter_regex='time=' --file=- --add_field site=org --add_field infra=ec2 --samplerate 10 --dynsampling level --dynsampling repository

